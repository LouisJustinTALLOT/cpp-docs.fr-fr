---
title: "Impossible de combiner SimplifiedChinese et VbStrConv.TraditionalChinese | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrArgument_StrConvSCandTC"
ms.assetid: d8e6a11b-f549-43b5-8337-0594340e1325
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de combiner SimplifiedChinese et VbStrConv.TraditionalChinese
Votre application essaie de combiner les membres de l’énumération `VbStrConv``SimplifiedChinese` et `TraditionalChinese`, qui s’excluent mutuellement.  
  
### Pour corriger cette erreur  
  
-   Supprimez  `VbStrConv.SimplifiedChinese` ou `VbStrConv.TraditionalChinese`.  
  
## Voir aussi  
 <xref:System.Globalization>   
 [NOTINBUILD Énumération VbStrConv](http://msdn.microsoft.com/fr-fr/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [Introduction aux applications internationales basées sur le .NET Framework](../Topic/Introduction%20to%20International%20Applications%20Based%20on%20the%20.NET%20Framework.md)