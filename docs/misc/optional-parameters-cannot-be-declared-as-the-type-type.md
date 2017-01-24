---
title: "Les param&#232;tres optionnels ne peuvent pas &#234;tre d&#233;clar&#233;s avec le type &#39;&lt;type&gt;&#39; | Microsoft Docs"
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
  - "bc30423"
  - "vbc30423"
helpviewer_keywords: 
  - "BC30423"
ms.assetid: 972dab8b-d91e-4a89-b822-2b8e4aadd25f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les param&#232;tres optionnels ne peuvent pas &#234;tre d&#233;clar&#233;s avec le type &#39;&lt;type&gt;&#39;
Les paramètres optionnels ne peuvent pas être du type de données d’une structure.  
  
 **ID d’erreur :** BC30423  
  
### Pour corriger cette erreur  
  
1.  Pour passer une structure à un paramètre optionnel, déclarez le paramètre en tant que `Object`.  
  
2.  Utilisez `CType` pour convertir le paramètre en ce type de structure dans la procédure.  
  
## Voir aussi  
 [Structures and Classes](../Topic/Structures%20and%20Classes%20\(Visual%20Basic\).md)   
 [CType, fonction](../Topic/CType%20Function%20\(Visual%20Basic\).md)