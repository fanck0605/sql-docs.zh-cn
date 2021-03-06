---
title: managed_backup sp_backup_master_switch （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_ backup_master_switch
- smart_admin.sp_backup_master_switch
- sp_ backup_master_switch_TSQL
- smart_admin.sp_backup_master_switch_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_ backup_master_switch
- smart_admin.sp_backup_master_switch
ms.assetid: 1ed2b2b2-c897-41cc-bed5-1c6bc47b9dd2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 242ef833cbb5a6a54b52fba0d1f435a7ca475cf0
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830361"
---
# <a name="managed_backupsp_backup_master_switch-transact-sql"></a>managed_backup sp_backup_master_switch （Transact-sql）
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  暂停或继续 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]。  
  
 使用此存储过程可临时暂停然后继续 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]。 这样确保在操作继续进行时所有配置设置保持不变并得以保留。 暂停 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 时，不执行保持期。 这意味着不检查是否应从存储中删除文件，或是否有备份文件损坏或日志链中断。  
  

  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```sql  
EXEC managed_backup.sp_backup_master_switch   
                     [@new_state = ] { 0 | 1}  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>形参  
 @state  
 设置 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 的状态。 @state参数为**BIT**。 将其值设置为 0 时，操作暂停；将其值设置为 1 时，操作继续进行。  
  
## <a name="return-code-value"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="security"></a>安全  
 介绍与语句相关的安全问题。包括“权限”小节（H3 标题）。 在适当时考虑包括其他“所有权链接”和“审核”小节。  
  
### <a name="permissions"></a>权限  
 要求具有**db_backupoperator**数据库角色的成员身份，具有**ALTER ANY CREDENTIAL**权限以及对**sp_delete_backuphistory**存储过程的**EXECUTE**权限。  
  
## <a name="examples"></a>示例  
 可使用下例在执行 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 的实例上暂停它：  
  
```  
Use msdb;  
GO  
EXEC managed_backup.sp_backup_master_switch @new_state=0;  
Go  
  
```  
  
 可使用下例继续 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]。  
  
```  
Use msdb;  
GO  
EXEC managed_backup.sp_backup_master_switch @new_state=1;  
Go  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [目标为 Microsoft Azure 的 SQL Server 托管备份](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  
