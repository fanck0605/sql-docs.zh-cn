---
title: sys. dm_exec_query_parallel_workers （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_parallel_workers_TSQL
- dm_exec_query_parallel_workers
- sys.dm_exec_query_parallel_workers_TSQL
- sys.dm_exec_query_parallel_workers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_parallel_workers dynamic management view
ms.assetid: 1d72cef1-22d8-4ae0-91db-6694fe918c9f
author: pelopes
ms.author: pelopes
manager: ajayj
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 000dd995427f8eafec759688db1ab76a6546b789
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "68263261"
---
# <a name="sysdm_exec_query_parallel_workers-transact-sql"></a>sys.dm_exec_query_parallel_workers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  返回每个节点的工作线程可用性信息。  
  
|名称|数据类型|说明|  
|----------|---------------|-----------------|  
|**node_id**|**int**|NUMA 节点 ID。|  
|**scheduler_count**|**int**|此节点上的计划程序数目。|  
|**max_worker_count**|**int**|并行查询的最大工作线程数。|  
|**reserved_worker_count**|**int**|并行查询保留的辅助角色数，以及所有请求使用的主辅助进程数。| 
|**free_worker_count**|**int**|可用于任务的工作线程数。<br /><br />**注意：** 每个传入请求使用至少1个辅助角色，从免费工作线程数中减去。  在负载过重的服务器上，免费辅助角色计数可能为负数。| 
|**used_worker_count**|**int**|并行查询使用的辅助进程数。|  
  
## <a name="permissions"></a>权限  

在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]上， `VIEW SERVER STATE`需要权限。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]高级层上，需要`VIEW DATABASE STATE`具有数据库中的权限。 在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]标准层和基本层上，需要**服务器管理员**或**Azure Active Directory 管理员**帐户。   
 
## <a name="examples"></a>示例  
  
### <a name="a-viewing-current-parallel-worker-availability"></a>A. 查看当前并行辅助角色可用性  

```sql 
SELECT * FROM sys.dm_exec_query_parallel_workers;  
```  
  
## <a name="see-also"></a>另请参阅  
 [动态管理视图和函数 &#40;Transact-sql&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [与执行相关的动态管理视图和函数 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys. dm_os_workers &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)
