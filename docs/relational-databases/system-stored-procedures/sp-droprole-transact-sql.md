---
title: sp_droprole （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droprole
- sp_droprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droprole
ms.assetid: 889ee074-00f8-40a9-bddb-d7d3ef0cbc19
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: df28493f6229a28b0f10d53bebad8bf031e63822
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833309"
---
# <a name="sp_droprole-transact-sql"></a>sp_droprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  从当前数据库中删除数据库角色。  
  
> [!IMPORTANT]  
>  在中 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ， **sp_droprole**已由 DROP ROLE 语句取代。 提供**sp_droprole**仅是为了兼容早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，在未来版本中可能不支持。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_droprole [ @rolename= ] 'role'  
```  
  
## <a name="arguments"></a>参数  
`[ @rolename = ] 'role'`要从当前数据库中删除的数据库角色的名称。 *role*是**sysname**，无默认值。 *角色*必须已存在于当前数据库中。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="remarks"></a>备注  
 只能使用**sp_droprole**删除数据库角色。  
  
 不能删除带有现有成员的数据库角色。 必须删除数据库角色的所有成员，然后才能删除该数据库角色。 若要从角色中删除用户，请使用**sp_droprolemember**。 如果任何用户仍是该角色的成员， **sp_droprole**将显示这些成员。  
  
 固定角色和**公共**角色无法删除。  
  
 如果角色拥有任何安全对象，则不能将其删除。 在删除拥有安全对象的应用程序角色之前，必须首先移交安全对象的所有权或将其删除。 使用 ALTER AUTHORIZATION 更改必须删除的对象的所有者。  
  
 不能在用户定义的事务中执行**sp_droprole** 。  
  
## <a name="permissions"></a>权限  
 需要对角色具有 CONTROL 权限。  
  
## <a name="examples"></a>示例  
 以下示例删除应用程序角色 `Sales`。  
  
```  
EXEC sp_droprole 'Sales';  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [安全存储过程 &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [DROP ROLE &#40;Transact-sql&#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-sql&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sp_dropapprole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropapprole-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
