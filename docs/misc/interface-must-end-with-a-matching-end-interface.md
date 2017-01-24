---
title: "&#39;Interface&#39; doit se terminer par un &#39;End Interface&#39; correspondant | Microsoft Docs"
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
  - "vbc30253"
  - "bc30253"
helpviewer_keywords: 
  - "BC30253"
ms.assetid: 0a2d5b70-997f-4926-ab79-4fdfa23042f7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Interface&#39; doit se terminer par un &#39;End Interface&#39; correspondant
Une instruction `Interface` se produit sans instruction `End Interface` correspondante. Vous devez utiliser une instruction `End Interface` pour terminer à la définition d’interface.  
  
 **ID d’erreur :** BC30253  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que les membres `Interface` sont correctement formatés.  
  
2.  Ajoutez une instruction `End Interface` à la fin de la définition d’interface.  
  
## Voir aussi  
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)