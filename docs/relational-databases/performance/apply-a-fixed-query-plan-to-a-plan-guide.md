---
title: 将固定查询计划应用到计划指南 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: bbf401f9-af7c-48e7-8a43-bf25e8af2fd7
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 8bb64d5a74fbc7b72c543a49fcf658caea6a2ef4
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2020
ms.locfileid: "67985069"
---
# <a name="apply-a-fixed-query-plan-to-a-plan-guide"></a>将现有查询计划应用到计划指南
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  您可以将现有查询计划应用到 OBJECT 或 SQL 类型的计划指南。 当您注意到对于特定查询现有的执行计划比优化器选择的计划执行得更好时，应用现有查询计划的计划指南将非常有用。  
  
 下面的示例为简单的临时 SQL 语句创建一个计划指南。 在计划指南中，直接在 `@hints` 参数中为查询指定 XML 显示计划，从而为该语句提供了所需的查询计划。 该示例首先通过执行 SQL 语句在计划缓存中生成一个计划。 对于此示例，假定所生成的计划就是所需的计划，不需要做进一步的查询优化。 此查询的 XML 显示计划可通过查询 `sys.dm_exec_query_stats`、 `sys.dm_exec_sql_text`和 `sys.dm_exec_text_query_plan` 动态管理视图获得，并可以分配给 `@xml_showplan` 变量。 然后，将 `@xml_showplan` 变量传递给 `sp_create_plan_guide` 语句中的 `@hints` 参数。 也可以使用 [sp_create_plan_guide_from_handle](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md) 存储过程从计划缓存中的查询计划中创建计划指南。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;  
GO  
DECLARE @xml_showplan nvarchar(max);  
SET @xml_showplan = (SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%');  
  
EXEC sp_create_plan_guide   
    @name = N'Guide1_from_XML_showplan',   
    @stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',   
    @type = N'SQL',  
    @module_or_batch = NULL,   
    @params = NULL,   
    @hints = @xml_showplan;  
GO  
```  
  
  
