---
title: 数据转换 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontrans.f1
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 9fb3d2b9e590e12b0a902a630b4c55a3baa9108f
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84939618"
---
# <a name="data-conversion-transformation"></a>数据转换
  数据转换将输入列中的数据转换为其他数据类型，然后将其复制到新的输出列。 例如，包可从多个源中提取数据，然后用此转换将列转换为目标数据存储所需的数据类型。 可以对单个输入列应用多个转换。  
  
 使用此转换，包可以执行下列类型的数据转换：  
  
-   更改数据类型。 有关详细信息，请参阅 [Integration Services 数据类型](../integration-services-data-types.md)。  
  
    > [!NOTE]  
    >  如果将数据转换为日期或日期时间数据类型，则输出列中的日期为 ISO 格式，即使区域设置首选项指定了不同格式时也是如此。  
  
-   设置字符串数据的列长度和数值数据的精度及小数位数。 有关详细信息，请参阅[精度、小数位数和长度 (Transact-SQL)](/sql/t-sql/data-types/precision-scale-and-length-transact-sql)。  
  
-   指定一个代码页。 有关详细信息，请参阅 [Comparing String Data](../comparing-string-data.md)。  
  
    > [!NOTE]  
    >  在包含字符串数据类型的列之间复制时，两列必须使用相同的代码页。  
  
 如果字符串数据的输出列长度小于其对应的输入列长度，则输出数据将被截断。 有关详细信息，请参阅 [数据中的错误处理](../error-handling-in-data.md)。  
  
 此转换有一个输入、一个输出和一个错误输出。  
  
## <a name="related-tasks"></a>Related Tasks  
 可以通过 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 设计器或以编程方式来设置属性。 有关在 SSIS 设计器中使用数据转换的信息，请参阅 [使用数据转换将数据转换为其他数据类型](data-conversion-transformation.md) 和 [数据转换编辑器](../../data-conversion-transformation-editor.md)。 有关如何以编程方式设置此转换的属性的信息，请参阅 [通用属性](../../common-properties.md) 和 [转换自定义属性](transformation-custom-properties.md)。  
  
## <a name="related-content"></a>相关内容  
 blogs.msdn.com 上的博客文章 [SSIS 2008 中数据类型转换技术之间的性能比较](https://techcommunity.microsoft.com/t5/datacat/performance-comparison-between-data-type-conversion-techniques/ba-p/305035)。  
  
## <a name="see-also"></a>另请参阅  
 [快速分析](../../fast-parse.md)   
 [数据流](../data-flow.md)   
 [Integration Services 转换](integration-services-transformations.md)  
  
  
