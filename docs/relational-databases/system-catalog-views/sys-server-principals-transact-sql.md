---
title: sys. server_principals （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_principals
- sys.server_principals_TSQL
- sys.server_principals
- server_principals_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_principals catalog view
ms.assetid: c5dbe0d8-a1c8-4dc4-b9b1-22af20effd37
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 408ad309ade858c800b79ee83993fda4fe78467a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "68133089"
---
# <a name="sysserver_principals-transact-sql"></a>sys.server_principals (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  每个服务器级别主体占一行。  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|name |**sysname**|主体的名称。 在服务器中是唯一的。|  
|**principal_id**|**int**|主体的 ID 号。 在服务器中是唯一的。|  
|**sid**|**varbinary （85）**|主体的 SID（安全标识符）。 如果是 Windows 主体，则它与 Windows SID 匹配。|  
|**type**|**char （1）**|主体类型：<br /><br /> S = SQL 登录名<br /><br /> U = Windows 登录名<br /><br /> G = Windows 组<br /><br /> R = 服务器角色<br /><br /> C = 映射到证书的登录名<br /><br /> K = 映射到非对称密钥的登录名|  
|**type_desc**|**nvarchar(60)**|主体类型的说明：<br /><br /> SQL_LOGIN<br /><br /> WINDOWS_LOGIN<br /><br /> WINDOWS_GROUP<br /><br /> SERVER_ROLE<br /><br /> CERTIFICATE_MAPPED_LOGIN<br /><br /> ASYMMETRIC_KEY_MAPPED_LOGIN|  
|**is_disabled**|**int**|1 = 禁用登录名。|  
|**create_date**|**datetime**|主体的创建时间。|  
|**modify_date**|**datetime**|上次修改主体定义的时间。|  
|**default_database_name**|**sysname**|该主体的默认数据库。|  
|**default_language_name**|**sysname**|该主体的默认语言。|  
|**credential_id**|**int**|与该主体关联的凭据的 ID。 如果没有与该主体关联的凭据，则 credential_id 将为 NULL。|  
|**owning_principal_id**|**int**|服务器角色的所有者的**principal_id** 。 如果主体不是服务器角色，则为 NULL。|  
|**is_fixed_role**|**bit**|如果主体是具有固定权限的内置服务器角色之一，则返回1。 有关详细信息，请参阅 [服务器级别角色](../../relational-databases/security/authentication-access/server-level-roles.md)。|  
  
## <a name="permissions"></a>权限  
 任何登录都可以查看自己的登录名称、系统登录和固定的数据库角色。 要查看其他登录，需要获取 ALTER ANY LOGIN 或有关登录的权限。 要查看用户定义的服务器角色，需要获取 ALTER ANY SERVER ROLE 或相关的角色成员身份。  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="examples"></a>示例  
 以下查询将列出明确对服务器主体授予或拒绝的权限。  
  
> [!IMPORTANT]  
>  固定服务器角色（除 public 之外）的权限不会出现在 sys. server_permissions 中。 因此，服务器主体可能具有此处未列出的其他权限。  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pe.state_desc, pe.permission_name   
FROM sys.server_principals AS pr   
JOIN sys.server_permissions AS pe   
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
## <a name="see-also"></a>另请参阅  
 [Transact-sql&#41;&#40;安全目录视图](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Transact-sql&#41;的目录视图 &#40;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [主体（数据库引擎）](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [权限层次结构（数据库引擎）](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
  
  
