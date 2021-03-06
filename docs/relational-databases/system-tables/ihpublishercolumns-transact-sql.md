---
title: IHpublishercolumns （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublishercolumns
- IHpublishercolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumns system table
ms.assetid: a5347750-224c-40d9-ae12-57e7213b7db9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6abe1290b0d635a615a4c83709a8e208bab2b487
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82813348"
---
# <a name="ihpublishercolumns-transact-sql"></a>IHpublishercolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublishercolumns**系统表表示在发布服务器上存储的元数据。 每个使用当前分发服务器从非 SQL Server 发布服务器复制的列都在该表中对应一行。 **IHpublishercolumns**中的数据类型信息特定于从中发布数据的非 SQL Server 数据库管理系统（DBMS）。 此表存储在分发数据库中。  
  
## <a name="definition"></a>定义  
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|标识已发布列。|  
|table_id****|**int**|标识列所属的[IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md)中的源表。|  
|**publisher_id**|**smallint**|标识正在发布该列的非 SQL Server 发布服务器。|  
|**name**|**sysname**|已发布列的名称。|  
|**column_ordinal**|**int**|按顺序标识列。|  
|type |**varchar(255)**|发布服务器上源列的列数据类型。|  
|**length**|**bigint**|发布服务器上源列的长度。|  
|**prec**|**int**|发布服务器上源列的精度。|  
|**scale**|**int**|发布服务器上源列的小数位数。|  
|**isnullable**|**bit**|指示列是否接受 NULL 值，其中**1**表示接受 null 值。|  
|**iscaptured**|**bit**|指示列上是否存在触发器，即使列没有在项目中发布，该列也可能存在。 如果值为**1** ，则表示该触发器存在于列上。|  
  
## <a name="see-also"></a>另请参阅  
 [异类数据库复制](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Transact-sql&#41;&#40;复制表](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Transact-sql&#41;&#40;复制视图](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sysarticlecolumns &#40;系统视图&#41; &#40;Transact-sql&#41;](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-sql&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
