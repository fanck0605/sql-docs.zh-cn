---
title: 从源代码管理打开解决方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- opening solutions
- solutions [SQL Server Management Studio], opening
ms.assetid: a96a1f0d-0183-4587-a3b0-4598309cbdd2
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0767df9d8ad010e17560b1f2b5e2e227d52a9f99
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285693"
---
# <a name="open-solutions-from-source-control"></a>从源代码管理打开解决方案
  可以使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 直接从源代码管理打开解决方案。 如果执行此操作，Studio 环境将在指定的位置创建最新版本解决方案文件的副本。  
  
 如果本地磁盘中没有解决方案的本地副本，则必须先从源代码管理打开项目，然后才能使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 签出解决方案或检索解决方案文件。  
  
> [!NOTE]  
>  如果已经有了要从源代码管理打开的解决方案的本地副本，系统会提示您覆盖本地副本。  
  
### <a name="to-open-a-solution-from-source-control"></a>若要从源代码管理打开解决方案  
  
1.  上**文件**菜单，依次指向**源代码管理**，然后单击**从源代码管理打开**。  
  
2.  如果出现提示，请登录到 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe。  
  
3.  在中**从 SourceSafe 创建本地项目**对话框框中，选择包含你想要打开，然后单击的解决方案的文件夹**确定**。  
  
4.  如果在本地磁盘驱动器上已存在解决方案的工作文件夹**文件夹中创建一个新项目**框发生更改，以标识本地目录。 如果不存在解决方案的工作文件夹，则可以键入或通过浏览找到要在其中打开解决方案的本地目录。  
  
5.  在中**打开的解决方案**对话框中，选择解决方案文件，然后单击**确定**。  
  
## <a name="see-also"></a>请参阅  
 [从源代码管理打开项目](../../2014/database-engine/open-projects-from-source-control.md)  
  
  