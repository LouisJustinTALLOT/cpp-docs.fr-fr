---
title: "&#39;.&#39; attendu | Microsoft Docs"
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
  - "bc30287"
  - "vbc30287"
helpviewer_keywords: 
  - "BC30287"
ms.assetid: 7d7b4934-b521-4ed3-b054-aeb71f8daacf
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;.&#39; attendu
Le code contient une clause `Handles` qui comprend un point d’exclamation \(`!`\).  
  
 **ID d’erreur :** BC30287  
  
### Pour corriger cette erreur  
  
1.  Si la clause `Handles` fait référence à un événement au sein d’un objet, utilisez un point \(`.`\) pour séparer l’objet de l’événement.  
  
     Cet exemple gère l’événement `Click` à partir de l’objet `Button1`.  
  
     [!code-vb[VbVbalrEventError#21](../misc/codesnippet/VisualBasic/dot-expected_1.vb)]  
  
## Voir aussi  
 [Handles](../Topic/Handles%20Clause%20\(Visual%20Basic\).md)