---
title: "&#39;Catch&#39; ne peut pas appara&#238;tre en dehors d’une instruction &#39;Try&#39;. | Microsoft Docs"
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
  - "bc30380"
  - "vbc30380"
helpviewer_keywords: 
  - "BC30380"
ms.assetid: 73ce950d-881f-4532-8024-40a4930abd32
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Catch&#39; ne peut pas appara&#238;tre en dehors d’une instruction &#39;Try&#39;.
`Catch` doit apparaître dans un bloc d’instruction `Try...Catch...Finally`. Soit vous avez une instruction `Catch` inutile dans votre bloc `Try`, soit votre instruction `Catch` apparaît en dehors des limites de son bloc `Try`.  
  
 **ID d’erreur :** BC30380  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’instruction `Catch` si elle n’est pas nécessaire, ou placez\-la dans un bloc d’instruction `Try...Catch...Finally`.  
  
## Voir aussi  
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Vue d’ensemble de la gestion structurée des exceptions pour Visual Basic](http://msdn.microsoft.com/fr-fr/bb81af80-a735-4873-9711-6151a48e418a)