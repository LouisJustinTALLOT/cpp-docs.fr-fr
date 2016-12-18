---
title: "La structure &#39;&lt;nom_structure&gt;&#39; ne peut pas contenir une instance d’elle-m&#234;me&#160;: &lt;erreur&gt; | Microsoft Docs"
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
  - "vbc30294"
  - "bc30294"
helpviewer_keywords: 
  - "BC30294"
ms.assetid: 17780e11-2425-4860-9345-b5db019d2bf3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La structure &#39;&lt;nom_structure&gt;&#39; ne peut pas contenir une instance d’elle-m&#234;me&#160;: &lt;erreur&gt;
Une structure déclare une variable et l’initialise avec une instance d’elle\-même.  
  
 Une structure peut contenir des instances d’autres structures, mais pas une instance interne d’elle\-même. En procédant ainsi, vous obtenez une récurrence infinie.  
  
 **ID d’erreur :** BC30294  
  
### Pour corriger cette erreur  
  
1.  Vérifiez l’orthographe de l’expression d’initialisation dans l’instruction de la déclaration.  
  
2.  Si vous voulez créer une autre instance de la même structure, vous devez la déclarer, puis la créer en dehors de la structure.  
  
## Voir aussi  
 [Structures](../Topic/Structures%20\(Visual%20Basic\).md)   
 [Structure Statement](../Topic/Structure%20Statement.md)