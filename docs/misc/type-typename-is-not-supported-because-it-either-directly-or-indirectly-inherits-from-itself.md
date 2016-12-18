---
title: "Le type &#39;&lt;nom_type&gt;&#39; n’est pas pris en charge, car il h&#233;rite directement ou indirectement de lui-m&#234;me | Microsoft Docs"
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
  - "bc30916"
  - "vbc30916"
helpviewer_keywords: 
  - "BC30916"
ms.assetid: cea33daf-1971-4b70-a01d-7d8b5c9e4269
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type &#39;&lt;nom_type&gt;&#39; n’est pas pris en charge, car il h&#233;rite directement ou indirectement de lui-m&#234;me
Une classe ou interface hérite d’elle\-même ou d’une autre classe ou interface qui finit par en hériter.  
  
 Visual Basic ne prend pas en charge l’héritage circulaire.  
  
 **ID d’erreur :** BC30916  
  
### Pour corriger cette erreur  
  
-   Modifiez la structure d’héritage pour qu’elle repose sur une classe de base ou interface qui n’hérite pas d’une autre classe ou interface.  
  
## Voir aussi  
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)