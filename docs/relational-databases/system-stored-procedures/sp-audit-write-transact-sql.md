---
title: sp_audit_write （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_audit_write
- sp_audit_write_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_audit_write
ms.assetid: 4c523848-1ce6-49ad-92b3-e0e90f24f1c2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ba751e5872f4f6fa4973674170d54a0dbc75f75a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833420"
---
# <a name="sp_audit_write-transact-sql"></a>sp_audit_write (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  将用户定义的审核事件添加到**USER_DEFINED_AUDIT_GROUP**。 如果未启用**USER_DEFINED_AUDIT_GROUP** ， **sp_audit_write**将被忽略。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
sp_audit_write [ @user_defined_event_id = ] user_defined_event_id
    [ , [ @succeeded = ] succeeded ]
    [ , [ @user_defined_information = ] 'user_defined_information' ]
    [ ; ]
```  
  
## <a name="arguments"></a>参数  
 `[ @user_defined_event_id = ] user_defined_event_id`  
 用户定义并记录在审核日志的**user_defined_event_id**列中的参数。 * \@ user_defined_event_id*类型为**smallint**。  
  
 `[ @succeeded = ] succeeded`  
 用户为指示事件是否成功而传递的参数。 它将出现在审核日志的成功列中。 `@succeeded`为**bit**。  
  
 `[ @user_defined_information = ] 'user_defined_information'`  
 由用户定义的文本，并且该文本将记录在审核日志的新的 user_defined_event_id 列中。 `@user_defined_information`为**nvarchar （4000）**。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
 失败是由不正确的输入参数或者未能写入目标审核日志导致的。  
  
## <a name="remarks"></a>备注  
 如果将**USER_DEFINED_AUDIT_GROUP**添加到服务器审核规范或数据库审核规范中，则**sp_audit_write**触发的事件将包括在审核日志中。  
  
## <a name="permissions"></a>权限  
 需要**公共**数据库角色的成员身份。  
  
## <a name="examples"></a>示例  
  
### <a name="a-creating-a-user-defined-audit-event-with-informational-text"></a>A. 创建具有信息文本的用户定义的审核事件  
 下面的示例创建一个审核事件，该事件具有 ID 27、成功值 0，并且包括可选信息文本。  
  
```  
EXEC sp_audit_write @user_defined_event_id =  27 ,   
              @succeeded =  0   
            , @user_defined_information = N'Access to a monitored object.' ;  
```  
  
### <a name="b--creating-a-user-defined-audit-event-without-informational-text"></a>B.  创建没有信息文本的用户定义的审核事件  
 下面的示例创建一个审核事件，该事件具有 ID 27、成功值 0，并且不包括可选信息文本或可选参数名称。  
  
```  
EXEC sp_audit_write 27, 0;  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [安全存储过程 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sys. server_principals &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sp_addrole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [CREATE USER &#40;Transact-sql&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [sp_dropuser &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_grantlogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
