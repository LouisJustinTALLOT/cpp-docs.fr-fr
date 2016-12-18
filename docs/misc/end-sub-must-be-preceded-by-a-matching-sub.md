---
title: "&#39;End Sub&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Sub&#39; correspondant. | Microsoft Docs"
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
  - "vbc30429"
  - "bc30429"
helpviewer_keywords: 
  - "BC30429"
ms.assetid: cf9d0cfe-5dfa-4f6d-9d10-69eb16e413e1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Sub&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Sub&#39; correspondant.
Une instruction `End Sub` apparaît dans votre code sans qu’une définition de procédure `Sub` correspondante ne la précède.  
  
 **ID d’erreur :** BC30429  
  
### Pour corriger cette erreur  
  
-   Supprimez l’instruction `End Sub` si elle est redondante.  
  
-   Fournissez la procédure `Sub` manquante, le cas échéant.  
  
-   Déplacez `End Sub` vers l’emplacement de code approprié.  
  
## Voir aussi  
 [Sub Procedures](../Topic/Sub%20Procedures%20\(Visual%20Basic\).md)   
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)