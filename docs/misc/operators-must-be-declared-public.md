---
title: "Les op&#233;rateurs doivent &#234;tre d&#233;clar&#233;s &#39;Public&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33011"
  - "bc33011"
helpviewer_keywords: 
  - "BC33011"
ms.assetid: 67fc0dee-4ef5-4afc-a63a-f7d20bce7954
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les op&#233;rateurs doivent &#234;tre d&#233;clar&#233;s &#39;Public&#39;
[Operator Statement](../Topic/Operator%20Statement.md) n’inclut pas le mot clé [Public](../Topic/Public%20\(Visual%20Basic\).md).  
  
 Une procédure `Operator` exige les deux mots clés `Public` et [Shared](../Topic/Shared%20\(Visual%20Basic\).md), et un opérateur de conversion nécessite également le mot clé [Widening](../Topic/Widening%20\(Visual%20Basic\).md) ou le mot clé [Narrowing](../Topic/Narrowing%20\(Visual%20Basic\).md).  
  
 **ID d’erreur :** BC33011  
  
### Pour corriger cette erreur  
  
-   Ajoutez le mot clé `Public` à l’instruction `Operator`.  
  
## Voir aussi  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)