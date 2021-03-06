---
title: PDOStatement::getColumnMeta | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c92a21cc-8e53-43d0-a4bf-542c77c100c9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cb7e9e37d568659a71917df66016f2333ed4be46
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2020
ms.locfileid: "76918803"
---
# <a name="pdostatementgetcolumnmeta"></a>PDOStatement::getColumnMeta
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

检索列的元数据。  
  
## <a name="syntax"></a>语法  
  
```  
  
array PDOStatement::getColumnMeta ( $column );  
```  
  
#### <a name="parameters"></a>parameters  
 $conn：（整数）要检索其元数据的列的从零开始的数。  
  
## <a name="return-value"></a>返回值  
包含列的元数据的关联阵列（键和值）。 有关数组中的字段的说明，请参阅“备注”部分。  
  
## <a name="remarks"></a>备注  
下表介绍 getColumnMeta 返回的数组中的字段。  
  
|名称|VALUES|  
|--------|----------|  
|native_type|指定列的 PHP 类型。 始终为字符串。|  
|driver:decl_type|指定用于表示数据库中的列值的 SQL 类型。 如果结果集中的列是函数的结果，则 PDOStatement::getColumnMeta 不会返回此值。|  
|flags|指定为此列设置的标志。 始终为 0。|  
|name|指定数据库中的列的名称。|  
|表|指定包含数据库中的列的表格名称。 始终为空白。|  
|len|指定列长度。|  
|精度|指定此列的数值精度。|  
|pdo_type|指定此列的类型，由 PDO::PARAM_* 常量表示。 Always PDO::PARAM_STR (2)。|  
  
已在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]的版本 2.0 中添加了对 PDO 的支持。  
  
## <a name="example"></a>示例  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$stmt = $conn->query("select * from Person.ContactType");  
$metadata = $stmt->getColumnMeta(2);  
var_dump($metadata);  
  
print $metadata['sqlsrv:decl_type'] . "\n";  
print $metadata['native_type'] . "\n";  
print $metadata['name'];  
?>  
```  
  
## <a name="sensitivity-data-classification-metadata"></a>敏感度数据分类元数据

从版本 5.8.0 开始，用户可以使用新的语句属性 `PDO::SQLSRV_ATTR_DATA_CLASSIFICATION` 通过 `PDOStatement::getColumnMeta`（需要 Microsoft ODBC Driver 17.4.2 或更高版本）来访问 Microsoft SQL Server 2019 中的[敏感度数据分类元数据](https://docs.microsoft.com/sql/relational-databases/security/sql-data-discovery-and-classification?view=sql-server-ver15&tabs=t-sql#subheading-4)。

请注意，默认情况下 `PDO::SQLSRV_ATTR_DATA_CLASSIFICATION` 属性为 `false`，但当设置为 `true` 时，将使用敏感度数据分类元数据（如果存在）填充上述数组字段 `flags`。 

以患者表为例：

```
CREATE TABLE Patients 
      [PatientId] int identity,
      [SSN] char(11),
      [FirstName] nvarchar(50),
      [LastName] nvarchar(50),
      [BirthDate] date)
```

我们可以将 SSN 和 BirthDate 列分类，如下所示：

```
ADD SENSITIVITY CLASSIFICATION TO [Patients].SSN WITH (LABEL = 'Highly Confidential - secure privacy', INFORMATION_TYPE = 'Credentials')
ADD SENSITIVITY CLASSIFICATION TO [Patients].BirthDate WITH (LABEL = 'Confidential Personal Data', INFORMATION_TYPE = 'Birthdays')
```

若要访问元数据，请在将 `PDO::SQLSRV_ATTR_DATA_CLASSIFICATION` 设置为 true 后使用 `PDOStatement::getColumnMeta`，如以下代码片段所示：

```
$options = array(PDO::SQLSRV_ATTR_DATA_CLASSIFICATION => true);
$tableName = 'Patients';
$tsql = "SELECT * FROM $tableName";
$stmt = $conn->prepare($tsql, $options);
$stmt->execute();
$numCol = $stmt->columnCount();

for ($i = 0; $i < $numCol; $i++) {
    $metadata = $stmt->getColumnMeta($i);
    $jstr = json_encode($metadata);
    echo $jstr . PHP_EOL;
}
```

所有列的元数据输出如下：

```
{"flags":{"Data Classification":[]},"sqlsrv:decl_type":"int identity","native_type":"string","table":"","pdo_type":2,"name":"PatientId","len":10,"precision":0}
{"flags":{"Data Classification":[{"Label":{"name":"Highly Confidential - secure privacy","id":""},"Information Type":{"name":"Credentials","id":""}}]},"sqlsrv:decl_type":"char","native_type":"string","table":"","pdo_type":2,"name":"SSN","len":11,"precision":0}
{"flags":{"Data Classification":[]},"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"FirstName","len":50,"precision":0}
{"flags":{"Data Classification":[]},"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"LastName","len":50,"precision":0}
{"flags":{"Data Classification":[{"Label":{"name":"Confidential Personal Data","id":""},"Information Type":{"name":"Birthdays","id":""}}]},"sqlsrv:decl_type":"date","native_type":"string","table":"","pdo_type":2,"name":"BirthDate","len":10,"precision":0}
```

如果我们通过将 `PDO::SQLSRV_ATTR_DATA_CLASSIFICATION` 设置为 `false`（默认情况）来修改上述代码片段，`flags` 字段将始终为 `0`，如下所示：

```
{"flags":0,"sqlsrv:decl_type":"int identity","native_type":"string","table":"","pdo_type":2,"name":"PatientId","len":10,"precision":0}
{"flags":0,"sqlsrv:decl_type":"char","native_type":"string","table":"","pdo_type":2,"name":"SSN","len":11,"precision":0}
{"flags":0,"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"FirstName","len":50,"precision":0}
{"flags":0,"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"LastName","len":50,"precision":0}
{"flags":0,"sqlsrv:decl_type":"date","native_type":"string","table":"","pdo_type":2,"name":"BirthDate","len":10,"precision":0}
```

      
## <a name="see-also"></a>另请参阅  
[PDOStatement 类](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
