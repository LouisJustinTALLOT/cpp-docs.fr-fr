---
title: "&#39;Continue&#39; doit &#234;tre suivi par &#39;Do&#39;, &#39;For&#39; ou &#39;While&#39; | Microsoft Docs"
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
  - "bc30781"
  - "vbc30781"
helpviewer_keywords: 
  - "BC30781"
ms.assetid: a0d5854d-ca44-4c6b-9458-4fc50d29281a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue&#39; doit &#234;tre suivi par &#39;Do&#39;, &#39;For&#39; ou &#39;While&#39;
Une instruction `Continue` doit être suivie de `Do`, `For` ou `While`, selon que l’instruction `Continue` apparaît dans une boucle `Do...Loop`, `For...Next` ou `While...End While`.  
  
 **ID d’erreur :** BC30781  
  
### Pour corriger cette erreur  
  
1.  Si l’instruction `Continue` se trouve dans une boucle `Do...Loop`, remplacez l’instruction par `Continue Do`.  
  
2.  Si l’instruction `Continue` se trouve dans une boucle `For...Next`, remplacez l’instruction par `Continue For`.  
  
3.  Si l’instruction `Continue` se trouve dans une boucle `While...End While`, remplacez l’instruction par `Continue While`.  
  
4.  Sinon, supprimez l’instruction `Continue`.  
  
## Voir aussi  
 [Continue Statement](../Topic/Continue%20Statement%20\(Visual%20Basic\).md)