---
title: sp_dropmergefilter （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergefilter_TSQL
- sp_dropmergefilter
helpviewer_keywords:
- sp_dropmergefilter
ms.assetid: 798586d7-05f3-4a5e-bea8-a34b7b52d0fd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c4e95865ea3c3b56c4d48036715b05a306f8b0a2
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830077"
---
# <a name="sp_dropmergefilter-transact-sql"></a>sp_dropmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  删除合并筛选器。 **sp_dropmergefilter**删除对要删除的合并筛选器定义的所有合并筛选器列。 此存储过程在发布服务器上对发布数据库执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "“主题链接”图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_dropmergefilter [ @publication= ] 'publication', [ @article= ] 'article'     , [ @filtername= ] 'filtername'  
    [ , [ @force_invalidate_snapshot= ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>参数  
`[ @publication = ] 'publication'`发布的名称。 *发布*为**sysname**，无默认值。  
  
`[ @article = ] 'article'`项目的名称。 *项目*是**sysname**，无默认值。  
  
`[ @filtername = ] 'filtername'`要删除的筛选器的名称。 *filtername*的值为**sysname**，无默认值。  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot`启用或禁用使快照失效的功能。 *force_invalidate_snapshot*是一**位**，默认值为**0**。  
  
 **0**指定对合并项目所做的更改不会导致快照无效。  
  
 **1**表示对合并项目所做的更改可能会导致快照无效。 如果是这种情况，则值为**1**时，将为新快照提供权限。  
  
`[ @force_reinit_subscription = ] force_reinit_subscription`启用或禁用将订阅标记为无效的功能。 *force_reinit_subscription*是一**位**，默认值为**0**。  
  
 **0**指定对合并项目筛选器所做的更改不会导致订阅无效。  
  
 **1**表示对合并项目筛选器的更改会导致订阅无效。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功）或**1** （失败）  
  
## <a name="remarks"></a>备注  
 **sp_dropmergefilter**用于合并复制。  
  
## <a name="permissions"></a>权限  
 只有**sysadmin**固定服务器角色的成员或**db_owner**固定数据库角色的成员才能执行**sp_dropmergefilter**。  
  
## <a name="see-also"></a>另请参阅  
 [更改发布和项目属性](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_changemergefilter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
