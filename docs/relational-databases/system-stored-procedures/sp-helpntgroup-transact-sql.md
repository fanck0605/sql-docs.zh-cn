---
title: sp_helpntgroup （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpntgroup
- sp_helpntgroup_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpntgroup
ms.assetid: 02b4f7c1-480a-436c-8bae-7a2488be45d2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 76da15896b5947d0fb66c717fcaeadcab045326e
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82834425"
---
# <a name="sp_helpntgroup-transact-sql"></a>sp_helpntgroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  报告有关在当前数据库中有帐户的 Windows 组的信息。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_helpntgroup [ [ @ntname= ] 'name' ]   
```  
  
## <a name="arguments"></a>参数  
`[ @ntname = ] 'name'`Windows 组的名称。 *名称*为**sysname**，默认值为 NULL。 *名称*必须是有权访问当前数据库的有效 Windows 组。 如果未指定*名称*，则会在输出中包含对当前数据库具有访问权限的所有 Windows 组。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="result-sets"></a>结果集  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**NTGroupName**|**sysname**|Windows 组的名称。|  
|**NTGroupId**|**smallint**|组标识符 (ID)。|  
|**SID**|**varbinary （85）**|**NTGroupName**的安全标识符（SID）。|  
|**HasDbAccess**|**int**|1 = Windows 组有权访问数据库。|  
  
## <a name="remarks"></a>备注  
 若要查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 当前数据库中的角色列表，请使用**sp_helprole**。  
  
## <a name="permissions"></a>权限  
 要求 **公共** 角色具有成员身份。  
  
## <a name="examples"></a>示例  
 以下示例输出有权访问当前数据库的 Windows 组的列表。  
  
```  
EXEC sp_helpntgroup;  
```  
  
## <a name="see-also"></a>另请参阅  
 [安全存储过程 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_helprole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_revokedbaccess &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
