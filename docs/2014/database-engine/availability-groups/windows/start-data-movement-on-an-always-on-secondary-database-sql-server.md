---
title: 启动 AlwaysOn 辅助数据库 (SQL Server) 的数据移动 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], databases
ms.assetid: 498eb3fb-6a43-434d-ad95-68a754232c45
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cbec6a7aa6c1ac92dbf64fe018800a223084e4e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37252789"
---
# <a name="start-data-movement-on-an-alwayson-secondary-database-sql-server"></a>启动 AlwaysOn 辅助数据库的数据移动 (SQL Server)
  本主题包含有关如何在将数据库添加到 AlwaysOn 可用性组后启动数据同步的信息。 对于每个新的主副本，必须在承载辅助副本的服务器实例上准备辅助数据库。 然后，必须将这些辅助数据库手动添加到可用性组。  
  
> [!NOTE]  
>  如果文件路径在每个承载可用性组的可用性副本的服务器实例上完全相同，则 [新建可用性组向导](use-the-availability-group-wizard-sql-server-management-studio.md)、 [将副本添加到可用性组向导](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)或 [将数据库添加到可用性组向导](availability-group-add-database-to-group-wizard.md) 可为你自动启动数据同步。  
  
 若要手动启动数据同步，需要依次连接到每个承载可用性组的辅助副本的服务器实例并完成以下步骤：  
  
1.  还原每个主数据库及其事务日志的当前副本（使用 RESTORE WITH NORECOVERY）。 您可以使用以下两种可选方法中的一种：  
  
    -   使用 RESTORE WITH NORECOVERY 手动还原主数据库的最新数据库备份，然后使用 RESTORE WITH NORECOVERY 还原各个后续日志备份。 在每个承载可用性组的辅助副本的服务器实例上执行此还原序列。  
  
         **详细信息：**  
  
         [为可用性组手动准备辅助数据库 (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
    -   如果您在将一个或多个日志传送主数据库添加到可用性组，则可能能够将一个或多个相应的辅助数据库从日志传送迁移到 AlwaysOn 可用性组。 迁移日志传送辅助数据库要求它使用与主数据库相同的数据库名称以及驻留在承载可用性组的辅助副本的服务器实例上。 此外，必须配置可用性组以便主副本成为备份的首选并且是执行备份的候选（即，具有 >0 的备份优先级）。 在备份作业已在主数据库上运行后，您将需要禁用该备份作业；并且在还原作业已在给定辅助数据库上运行后，将需要禁用还原作业。  
  
        > [!NOTE]  
        >  在您为可用性组创建了所有辅助数据库后，如果您想要在辅助副本上执行备份，将需要重新配置该可用性组的自动备份首选项。  
  
         **详细信息：**  
  
         [从迁移的先决条件日志传送到 AlwaysOn 可用性组&#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
         [配置可用性副本备份 (SQL Server)](configure-backup-on-availability-replicas-sql-server.md)  
  
2.  尽快将每个新准备的辅助数据库加入可用性组。  
  
     **详细信息：**  
  
     [将辅助数据库联接到可用性组 (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
##  <a name="LaunchWiz"></a> 相关任务  
  
-   [使用“新建可用性组”对话框 (SQL Server Management Studio)](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [使用“将副本添加到可用性组向导”(SQL Server Management Studio)](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [使用“将数据库添加到可用性组向导”(SQL Server Management Studio)](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a>请参阅  
 [AlwaysOn 可用性组概述&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  