---
title: "Les param&#232;tres de type ne peuvent pas &#234;tre sp&#233;cifi&#233;s pour cette d&#233;claration | Microsoft Docs"
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
  - "vbc32065"
  - "bc32065"
helpviewer_keywords: 
  - "BC32065"
ms.assetid: 94cfe3de-74fd-4a2c-9246-ec4a05b73d55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les param&#232;tres de type ne peuvent pas &#234;tre sp&#233;cifi&#233;s pour cette d&#233;claration
Un élément de programmation est déclaré avec une liste de paramètres de type, mais l’élément de programmation ne peut pas être un type générique.  
  
 Les propriétés, les opérateurs, les événements et les constructeurs comptent parmi les éléments de programmation qui ne peuvent pas être génériques. Le fait de déclarer l’un de ces éléments avec une liste de paramètres de type génère cette erreur.  
  
 **ID d’erreur :** BC32065  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé `Of` et les paramètres de type de la déclaration.  
  
## Voir aussi  
 [Types génériques Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)