---
title: close 方法 (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.close
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f0f26585-bdf7-4737-b434-8c7e115c8e94
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 64ad1bcc06af74296b441fcd0b22cf488c58ef8a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923668"
---
# <a name="close-method-sqlserverconnection"></a>close 方法 (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  立即释放此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象的数据库和 JDBC 资源，而非等待它们自动释放。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>备注  
 此 close 方法是由 java.sql.Connection 接口中的 close 方法指定的。  
  
 在事务中间调用 close 方法将回滚该事务。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerConnection 成员](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 类](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
