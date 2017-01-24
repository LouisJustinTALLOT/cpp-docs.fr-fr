---
title: "&#39;End Function&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Function&#39; correspondant | Microsoft Docs"
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
  - "bc30430"
  - "vbc30430"
helpviewer_keywords: 
  - "BC30430"
ms.assetid: de66a6b4-0321-45c2-aca0-87d2b4244b31
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Function&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Function&#39; correspondant
Une instruction `End Function` apparaît dans votre code sans qu’une définition de procédure `Function` correspondante ne la précède.  
  
 **ID d’erreur :** BC30430  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’instruction `End Function` si elle est redondante.  
  
2.  Fournissez la procédure `Function` manquante, le cas échéant.  
  
3.  Déplacez `End Function` vers l’emplacement de code approprié.  
  
## Voir aussi  
 [Function, procédures](../Topic/Function%20Procedures%20\(Visual%20Basic\).md)   
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)