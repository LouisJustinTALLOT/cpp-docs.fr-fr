---
title: "&#39;While&#39; doit se terminer par un &#39;End While&#39; correspondant | Microsoft Docs"
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
  - "bc30082"
  - "vbc30082"
helpviewer_keywords: 
  - "BC30082"
ms.assetid: 50b722b1-906f-4cb1-b5d4-fefab2ba3907
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;While&#39; doit se terminer par un &#39;End While&#39; correspondant
Il existe une occurrence d’instruction `While` sans instruction `End While` correspondante. Vous devez utiliser une instruction `End While` pour terminer le bloc `While`.  
  
 **ID d’erreur :** BC30082  
  
### Pour corriger cette erreur  
  
1.  Si ce bloc `While` fait partie d’un ensemble de blocs `While` imbriqués, vérifiez que chaque bloc se termine correctement.  
  
2.  Ajoutez une instruction `End While` à la fin du bloc `While`.  
  
## Voir aussi  
 [While...End While Statement](../Topic/While...End%20While%20Statement%20\(Visual%20Basic\).md)