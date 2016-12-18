---
title: "Les &#233;v&#233;nements des interfaces ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;&lt;implements&gt;&#39; | Microsoft Docs"
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
  - "bc30688"
  - "vbc30688"
helpviewer_keywords: 
  - "BC30688"
ms.assetid: 577823c1-815c-4f1c-9177-4bbf73fa92db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les &#233;v&#233;nements des interfaces ne peuvent pas &#234;tre d&#233;clar&#233;s &#39;&lt;implements&gt;&#39;
Les événements déclarés dans des interfaces ne peuvent pas implémenter les événements d’autres interfaces.  
  
 **ID d’erreur :** BC30688  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’instruction `Implements`.  
  
2.  Implémentez l’événement à l’intérieur d’une classe ou d’une structure.  
  
## Voir aussi  
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)