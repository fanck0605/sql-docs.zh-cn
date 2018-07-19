---
title: SQL Server Browser 属性 （在选项卡上的日志） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bacd58650b9c86a455714cfc464b9b995396a83e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37273773"
---
# <a name="sql-server-browser-properties-log-on-tab"></a>SQL Server 浏览器属性（“登录”选项卡）
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浏览器程序以服务的形式在服务器上运行。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浏览器侦听对 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源的传入请求，并提供计算机上安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的相关信息。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浏览器使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 解析协议 (SSRP) 侦听 UDP 端口，并接受未经身份验证的请求。  
  
 对帐户密码的更改立即生效，无需重新启动服务。  
  
## <a name="options"></a>“常规”  
 **本地系统帐户**  
 在本地系统帐户的安全上下文中运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。 请尽可能使用低权限帐户。  
  
 **本帐户**  
 指定一个使用 Windows 身份验证的本地用户帐户或域用户帐户。 建议使用具有最低服务权限的域用户帐户。 有关选择帐户的信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“设置 Windows 服务帐户”。  
  
 **“浏览”**  
 浏览用户或内置安全主体。  
  
> [!IMPORTANT]  
>  使用低权限帐户。 有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务所需权限的信息，请参阅 [SQL Server Browser 服务](../../../2014/tools/configuration-manager/sql-server-browser-service.md)中的“安全性”部分。  
  
 **密码**  
 输入安全主体的密码。  
  
 **确认密码**  
 确认安全主体的密码。  
  
 **服务状态**  
 指示此服务是正在运行、已停止还是已禁用。 **“...”** 指示状态更改被挂起。  
  
 **开始**  
 启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。  
  
 **停止**  
 停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。  
  
 **暂停**  
 暂停 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。  
  
 **恢复**  
 恢复暂停的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。  
  
## <a name="see-also"></a>请参阅  
 [SQL Server Browser 服务](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  