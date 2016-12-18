---
title: "&#39;Exit Property&#39; n’est pas valide dans un Function ou Sub | Microsoft Docs"
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
  - "vbc30066"
  - "bc30066"
helpviewer_keywords: 
  - "BC30066"
ms.assetid: 09e7e766-e35d-4282-b949-d227f733f950
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Property&#39; n’est pas valide dans un Function ou Sub
`Exit Property` apparaît dans une procédure `Function` ou `Sub`. Une instruction `Exit` doit correspondre au bloc dans lequel elle apparaît.  
  
 **ID d’erreur :** BC30066  
  
### Pour corriger cette erreur  
  
-   Remplacez `Exit Property` par l’instruction `Exit Function` ou `Exit Sub` selon les besoins.  
  
## Voir aussi  
 [Sub Procedures](../Topic/Sub%20Procedures%20\(Visual%20Basic\).md)   
 [Function, procédures](../Topic/Function%20Procedures%20\(Visual%20Basic\).md)   
 [Procédures de propriété](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)