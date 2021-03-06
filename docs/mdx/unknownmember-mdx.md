---
title: "UnknownMember (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2016"
ms.prod: analysis-services
ms.prod_service: "analysis-services"
ms.service: ""
ms.component: ""
ms.reviewer: ""
ms.suite: "pro-bi"
ms.technology: 
  
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "UnknownMember"
dev_langs: 
  - "kbMDX"
helpviewer_keywords: 
  - "UnknownMember function"
ms.assetid: 5ae39cbe-65c8-4a59-9548-71b28ecf6eb5
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
ms.workload: "Inactive"
---
# UnknownMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Returns the unknown member associated with a level or member.  
  
## Syntax  
  
```  
  
Member expression syntax  
Member_Expression.UnknownMember  
  
Hierarchy_expression syntax  
Hierarchy_Expression.UnknownMember  
```  
  
## Arguments  
 *Member_Expression*  
 A valid Multidimensional Expressions (MDX) expression that returns a member.  
  
 *Hierarchy_Expression*  
 A valid Multidimensional Expressions (MDX) expression that returns a hierarchy.  
  
## Remarks  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates an unknown member to associate fact table data with a hierarchy when the hierarchy is not known. The unknown member can be at one of the following levels:  
  
-   At the top level for attribute hierarchies that are not aggregated.  
  
-   At the first level below the **All** level for natural hierarchies.  
  
-   At any level for unnatural hierarchies.  
  
 If a member expression is specified, the **UnknownMember** function returns the unknown member child of the specified member. If the specified member does not exist, the function returns null.  
  
 If a hierarchy expression is specified, the **UnknownMember** function returns the unknown member at the top level if one exists.  
  
 If the unknown member does not exist on the level or member, the **UnknownMember** function creates a null member.  
  
> [!NOTE]  
>  If the unknown member does not exist on the hierarchy or member, an error is generated.  
  
## Examples  
 The following example returns the unknown member for the All Products member in the Product attribute hierarchy for all members of the Measures dimension.  
  
```  
SELECT [Product].[Product].[All Products].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
 The following example returns the unknown member for the Product Categories hierarchy for all members of the Measures dimension.  
  
```  
SELECT [Product].[Product Categories].UnknownMember  
    ON Columns,  
[Measures].Members  
    ON Rows  
FROM [Adventure Works]  
  
```  
  
## See Also  
 [MDX Function Reference &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
