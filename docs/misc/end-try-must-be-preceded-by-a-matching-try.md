---
title: "&#39;End Try&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Try&#39; correspondant | Microsoft Docs"
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
  - "bc30383"
  - "vbc30383"
helpviewer_keywords: 
  - "BC30383"
ms.assetid: 1d13357a-ab44-4082-b204-6e2e94f4774e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Try&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Try&#39; correspondant
L’instruction `End``Try` permet de terminer un bloc `Try` ; elle ne peut donc figurer qu’à la fin du bloc. Soit vous avez une instruction `End Try` redondante, soit votre instruction `End``Try` apparaît en dehors des limites de son bloc `Try` correspondant.  
  
 **ID d’erreur :** BC30383  
  
### Pour corriger cette erreur  
  
1.  Recherchez et supprimez l’instruction `End Try` inutile.  
  
2.  Déplacez `End Try` vers l’emplacement approprié dans votre code.  
  
## Voir aussi  
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Vue d’ensemble de la gestion structurée des exceptions pour Visual Basic](http://msdn.microsoft.com/fr-fr/bb81af80-a735-4873-9711-6151a48e418a)