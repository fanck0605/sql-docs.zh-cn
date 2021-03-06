---
title: MSSQLSERVER_30053 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 8ad23889-e243-4bd7-bc3e-150403399d89
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 02d6262f93ef3dbbc9834053f864046b4dca30f2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "85033979"
---
# <a name="mssqlserver_30053"></a>MSSQLSERVER_30053
    
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|30053|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|FTXT_QUERY_E_WORDBREAKINGTIMEOUT|  
|消息正文|全文查询字符串出现断字超时。 如果断字器长时间处理全文查询字符串或服务器上有大量查询正在运行，则会发生这种情况。 请在负荷较轻的情况下再次尝试运行此查询。|  
  
## <a name="explanation"></a>说明  
 在以下情况下会发生断字超时错误：  
  
-   查询语言的断字符配置不正确；例如，其注册表设置不正确。  
  
-   特定查询字符串的断字符工作不正常。  
  
-   断字符为特定查询字符串返回过多数据。 过多的数据将被视为潜在的缓冲区溢出攻击，并会关闭承载断字服务的筛选器后台进程 (fdhost.exe)。  
  
-   筛选器后台进程配置不正确。  
  
     最常见的配置问题是密码过期或阻止筛选器后台帐户登录的域策略。  
  
-   服务器实例上运行的查询工作负荷很重；例如，断字器长时间处理全文查询字符串或服务器上有大量查询正在运行。 请注意，此原因发生的可能性最低。  
  
## <a name="user-action"></a>用户操作  
 针对超时的可能原因选择适当的用户操作，如下所示：  
  
|可能的原因|用户操作|  
|--------------------|-----------------|  
|查询语言的断字符配置不正确。|如果使用的是第三方断字符，则该断字符在操作系统中的注册可能不正确。 在这种情况下，请重新注册断字符。 有关详细信息，请参阅[将搜索功能所使用的断字符还原到以前的版本](../search/revert-the-word-breakers-used-by-search-to-the-previous-version.md)。|  
|特定查询字符串的断字符工作不正常。|如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持断字符，请与 Microsoft 客户服务与支持部门联系。|  
|断字符为特定查询字符串返回过多数据。|如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持断字符，请与 Microsoft 客户服务与支持部门联系。|  
|筛选器后台进程配置不正确。|请确保使用的是当前密码，并且域策略不会阻止筛选器后台帐户登录。|  
|服务器实例上运行的查询工作负荷很重。|请在负荷较轻的情况下再次尝试运行此查询。|  
  
## <a name="see-also"></a>另请参阅  
 [设置全文筛选器后台程序启动器的服务帐户](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)   
 [全文搜索](../search/full-text-search.md)   
 [sp_help_fulltext_system_components &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql)   
 [配置和管理断字符和词干分析器以便搜索](../search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [配置和管理搜索筛选器](../search/configure-and-manage-filters-for-search.md)  
  
  
