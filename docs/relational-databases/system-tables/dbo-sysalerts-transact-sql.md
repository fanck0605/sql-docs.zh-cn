---
title: dbo. sysalerts （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysalerts
- sysalerts_TSQL
- dbo.sysalerts_TSQL
- sysalerts
dev_langs:
- TSQL
helpviewer_keywords:
- sysalerts system table
ms.assetid: a2c2f50d-61f3-4951-996a-add5ad092cc2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 277cd9ae3fdbe2414c9c3eb96208e79730ebdde6
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82813883"
---
# <a name="dbosysalerts-transact-sql"></a>dbo.sysalerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  每个警报在表中各占一行。 警报是为响应事件而发送的消息。 警报可向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 环境之外转发消息，警报可以是电子邮件或寻呼消息。 警报还可以生成任务。  该表存储在**msdb**数据库中。
  
|列名称|数据类型|说明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|警报 ID。|  
|**name**|**sysname**|警报名称。|  
|**event_source**|**nvarchar （100）**|事件源：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。|  
|**event_category_id**|**int**|保留供将来使用。|  
|**event_id**|**int**|保留供将来使用。|  
|**message_id**|**int**|用户定义的消息 ID 或对触发此警报的**sysmessages**消息的引用。|  
|severity |**int**|触发此警报的严重级别。|  
|**能够**|**tinyint**|警报的状态：<br /><br /> **0** = 禁用。<br /><br /> **1** = 已启用。|  
|**delay_between_responses**|**int**|此警报的两个通知间的等待时间（以秒为单位）。|  
|**last_occurrence_date**|**int**|警报的上次发生（日期）。|  
|**last_occurrence_time**|**int**|警报的上次发生（时间）。|  
|**last_response_date**|**int**|警报的上次通知（日期）。|  
|**last_response_time**|**int**|警报的上次通知（时间）。|  
|**notification_message**|**nvarchar(512)**|与警报一起发送的其他信息。|  
|**include_event_description**|**tinyint**|表示是否通过电子邮件、寻呼程序或 Net send 发送事件描述的位掩码。 有关值，请参阅下图。|  
|**database_name**|**nvarchar(512)**|此警报必须在其中发生才能触发该警报的数据库。|  
|**event_description_keyword**|**nvarchar （100）**|为触发警报而必须匹配的错误模式。|  
|**occurrence_count**|**int**|此警报的发生次数。|  
|**count_reset_date**|**int**|Day （date） count 将重置为**0**。|  
|**count_reset_time**|**int**|时间计数将重置为**0**。|  
|**job_id**|**uniqueidentifier**|此警报发生时执行的任务的 ID。|  
|**has_notification**|**int**|警报发生时接收电子邮件通知的操作员数。|  
|**flag**|**int**|保留。|  
|**performance_condition**|**nvarchar(512)**|保留。|  
|**category_id**|**int**|保留。|  
  
 ## <a name="remarks"></a>备注

下表显示 include_event_description 位掩码的值。 该十进制值由 sysalerts 返回。 

|Decimal | binary | 含义 |
|------|------|------|
|0 |0000 |无消息 |
|1 |0001 |电子邮件 |
|2 |0010 |pager |
|3 |0011 |寻呼和电子邮件 |
|4 |0100 |Net send |
|5 |0101 |网络发送和电子邮件 |
|6 |0110 |网络发送和寻呼 |
|7 |0111 |Net send、寻呼和电子邮件 |
  
