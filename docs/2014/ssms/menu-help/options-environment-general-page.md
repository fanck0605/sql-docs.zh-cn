---
title: 选项（"环境-常规" 页） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.SQLEnvironmentOptions
ms.assetid: c32ccdb8-2cf8-4c78-b474-a3abd3dbbd13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2b215ff16f5e4a42a6d43f0a6e5f9758f158a682
ms.sourcegitcommit: 18a7c77be31f9af92ad9d0d3ac5eecebe8eec959
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2020
ms.locfileid: "83859833"
---
# <a name="options-environment-general-page"></a>选项（“环境”-“常规”页）
  使用“选项”  对话框可以配置 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 启动操作、常规窗口管理选项和其他常规设置。 在“工具”  菜单上，单击“选项”  ，展开“环境”  文件夹，再单击“常规”  。  
  
## <a name="ui-element-list"></a>UI 元素列表  
 **启动时**  
 选择 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在启动时执行的操作。 选项包括：  
  
-   “打开对象资源管理器”****，如果选择此选项，将在启动时提示输入连接信息，然后打开对象资源管理器。  
  
-   “打开新查询窗口”****，如果选择此选项，将在启动时提示输入连接信息，然后打开 SQL 查询编辑器。  
  
-   “打开对象资源管理器和新查询”****，如果选择此选项，将在启动时提示输入连接信息，然后利用该连接打开对象资源管理器和 SQL 查询编辑器。  
  
-   “打开空环境”****，如果选择此选项，将在启动时打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，但不打开 SQL 查询编辑器窗口，并且不会将对象资源管理器连接到服务器。  
  
 **在对象资源管理器中隐藏系统对象**  
 如果选中此复选框，将从对象资源管理器内的树视图中删除系统数据库、系统表、系统视图和系统存储过程。 系统函数和系统数据类型将不隐藏。 此选项仅适用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例，并且不会影响对象资源管理器中已连接的服务器。  
  
## <a name="environment-layout"></a>环境布局  
 您必须关闭并重新打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，才能在选项卡式文档和多文档界面 (MDI) 环境模式之间切换。  
  
 **选项卡式文档**  
 如果选择此选项，文档窗口将在编辑器内以选项卡形式显示在一起。 在多个打开的文档之间进行组织和切换时，选项卡式文档窗口非常有用。  
  
 **MDI 环境**  
 选择此选项将在 MDI 环境中打开文档。 使用 MDI 文档窗口对于节省屏幕空间非常有用，而在选项卡式文档环境下，其中的选项卡会占用这些屏幕空间。 在 MDI 模式下，可以通过按 Ctrl+Tab 在文档之间进行切换，也可以使用“窗口”**** 菜单上的磁贴选项。  
  
## <a name="docked-tool-window-behavior"></a>停靠工具窗口行为  
 **“关闭”按钮只影响活动选项卡**  
 指定在选中此复选框时，仅关闭当前具有焦点的工具窗口，而非关闭停靠的所有工具窗口。 默认情况下，此复选框处于选中状态。  
  
 **“自动隐藏”按钮只影响活动选项卡**  
 指定在选中此复选框时，仅自动隐藏当前具有焦点的工具窗口，而非自动隐藏停靠的所有工具窗口。 默认情况下，此复选框已清除。  
  
## <a name="display"></a>显示  
 **显示 n 个文件(在最近使用的列表中)**  
 自定义“文件”**** 菜单上显示的最近所使用项目和文件的数量。 键入一个介于 1 和 24 之间的数字。 默认值为 4。 通过此方法可以轻松地检索最近使用的脚本项目和文件。  
  
  
