---
title: "&#39;For&#39; doit se terminer par un &#39;Next&#39; correspondant | Microsoft Docs"
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
  - "vbc30084"
  - "bc30084"
helpviewer_keywords: 
  - "BC30084"
ms.assetid: 4c5e49c2-7343-4487-b5f8-a38c97ba895b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;For&#39; doit se terminer par un &#39;Next&#39; correspondant
Il existe une occurrence d’instruction `For` sans instruction `Next` correspondante. Vous devez utiliser une instruction `Next` pour terminer la boucle `For`.  
  
 **ID d’erreur :** BC30084  
  
### Pour corriger cette erreur  
  
-   Si cette boucle `For` fait partie d’un ensemble de boucles imbriquées, vérifiez que chaque boucle est correctement terminée.  
  
-   Ajoutez une instruction `Next` à la fin de la boucle `For`.  
  
## Voir aussi  
 [For...Next, instruction](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)