---
title: "&#39;Enum&#39; doit se terminer par un &#39;End Enum&#39; correspondant | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30185"
  - "bc30185"
helpviewer_keywords: 
  - "BC30185"
ms.assetid: 43dd759c-1207-4dcc-b2e2-478d91e6f2f8
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Enum&#39; doit se terminer par un &#39;End Enum&#39; correspondant
Une instruction `Enum` se produit sans instruction `End Enum` correspondante. Vous devez utiliser une instruction `End Enum` pour terminer l’énumération.  
  
 **ID d’erreur :** BC30185  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que les membres `Enum` sont mis en forme correctement.  
  
2.  Ajoutez une instruction `End Enum` pour terminer l’énumération.  
  
## Voir aussi  
 [Enum Statement](../Topic/Enum%20Statement%20\(Visual%20Basic\).md)