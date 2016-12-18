---
title: "&#39;Catch&#39; ne peut pas appara&#238;tre apr&#232;s &#39;Finally&#39; dans une instruction &#39;Try&#39; | Microsoft Docs"
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
  - "vbc30379"
  - "bc30379"
helpviewer_keywords: 
  - "BC30379"
ms.assetid: 33d1278b-cf10-4c66-aaf8-08a4372f370b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Catch&#39; ne peut pas appara&#238;tre apr&#232;s &#39;Finally&#39; dans une instruction &#39;Try&#39;
Une instruction `Catch` apparaît dans le code après `Finally` qui termine un bloc d’instruction `Try`.`Catch` doit apparaître dans un bloc d’instruction `Try...Catch...Finally`.  
  
 **ID d’erreur :** BC30379  
  
### Pour corriger cette erreur  
  
1.  Déplacez l’instruction `Catch` vers un emplacement plus approprié dans le code.  
  
## Voir aussi  
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Vue d’ensemble de la gestion structurée des exceptions pour Visual Basic](http://msdn.microsoft.com/fr-fr/bb81af80-a735-4873-9711-6151a48e418a)