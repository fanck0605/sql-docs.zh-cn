---
title: Excel 自定义属性 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bdcc72b8-8950-47bd-88bf-5db6d48cc6bf
author: janinezhang
ms.author: janinez
ms.openlocfilehash: d03e321ddacd2e033880420f427145c99d30ff88
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84915727"
---
# <a name="excel-custom-properties"></a>Excel 自定义属性
  **源自定义属性**  
  
 Excel 源具有自定义属性和所有数据流组件通用的属性。  
  
 下表介绍 Excel 源的自定义属性。 所有属性均可读/写。  
  
|属性名称|数据类型|说明|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer|用来访问数据库的模式。 可能的值为 "**打开行集**"、"**从变量打开行集**"、 `SQL Command` 和 "来自变量的**SQL 命令**" 默认值为 **“打开行集”** 。|  
|CommandTimeout|Integer|命令超时之前的秒数。如果值为 0，则表示无限期超时。<br /><br /> **注意** ：此属性未在 **Excel 源编辑器**中提供，但可以使用 **高级编辑器**进行设置。|  
|OpenRowset|String|用来打开行集的数据库对象的名称。|  
|OpenRowsetVariable|String|该变量包含用来打开行集的数据库对象的名称。|  
|ParameterMapping|String|从 SQL 命令中的参数到变量的映射。|  
|SqlCommand|String|要执行的 SQL 命令。|  
|SqlCommandVariable|String|包含要执行的 SQL 命令的变量。|  
  
 Excel 源的输出和输出列没有自定义属性。  
  
 有关详细信息，请参阅 [Excel Source](excel-source.md)。  
  
 **目标自定义属性**  
  
 Excel 目标具有自定义属性和所有数据流组件通用的属性。  
  
 下表介绍 Excel 目标的自定义属性。 所有属性均可读/写。  
  
|属性名称|数据类型|说明|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer（枚举）|一个指定目标如何访问其目标数据库的值。<br /><br /> 此属性可以具有下列值之一：<br /><br /> `OpenRowset`（0）-提供表或视图的名称。<br /><br /> `OpenRowset from Variable`（1）-提供包含表或视图名称的变量的名称。<br /><br /> `OpenRowset Using Fastload`（3）-提供表或视图的名称。<br /><br /> `OpenRowset Using Fastload from Variable`（4）-提供包含表或视图名称的变量的名称。<br /><br /> `SQL Command`（2）-需要提供 SQL 语句。|  
|CommandTimeout|Integer|SQL 命令在超时前可以运行的最大秒数。值 **0** 表示不限制时间。 此属性的默认值为 **0**。<br /><br /> 注意：此属性在 Excel 目标编辑器  中未提供，但可以使用“高级编辑器”  进行设置。|  
|FastLoadKeepIdentity|Boolean|该值指定加载数据时是否复制标识值。 此属性仅对其中一个快速加载选项可用。 此属性的默认值为 **False**。|  
|FastLoadKeepNulls|Boolean|一个值，指定加载数据时是否复制 Null 值。 此属性仅对其中一个快速加载选项可用。 此属性的默认值为 **False**。|  
|FastLoadMaxInsertCommitSize|Integer|指定 Excel 目标在快速加载操作期间尝试提交的批大小的值。 默认值为 **2147483647**。 值 **0** 指示处理所有行后的单个提交操作。|  
|FastLoadOptions|String|快速加载选项的集合。 快速加载选项包括锁定表和检查约束。 可以指定其中的一个，或同时指定两个，或不指定其中的任何一个。<br /><br /> 注意：此属性的某些选项未在 Excel 目标编辑器  中提供，但可以使用“高级编辑器”  进行设置。|  
|OpenRowset|String|当 AccessMode 为时 `OpenRowset` ，为 Excel 目标访问的表或视图的名称。|  
|OpenRowsetVariable|String|当 AccessMode 为时 `OpenRowset from Variable` ，为包含 Excel 目标访问的表或视图名称的变量的名称。|  
|SqlCommand|String|当 AccessMode 为时 `SQL Command` ，Excel 目标用于指定数据的目标列的 transact-sql 语句。|  
  
 Excel 目标的输入和输入列没有自定义属性。  
  
 有关详细信息，请参阅 [Excel Destination](excel-destination.md)。  
  
## <a name="see-also"></a>另请参阅  
 [Common Properties](../common-properties.md)  
  
  
