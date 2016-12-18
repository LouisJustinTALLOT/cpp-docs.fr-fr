---
title: "Les instructions &#39;Namespace&#39; ne peuvent intervenir qu’au niveau du fichier ou de l’espace de noms | Microsoft Docs"
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
  - "bc30618"
  - "vbc30618"
helpviewer_keywords: 
  - "BC30618"
ms.assetid: bcd365a4-5d84-4c3c-83dc-40cb4c47f73b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les instructions &#39;Namespace&#39; ne peuvent intervenir qu’au niveau du fichier ou de l’espace de noms
Les instructions `Namespace` doivent apparaître après les instructions `Option`, les instructions `Imports` et les attributs globaux, mais avant toutes les autres déclarations dans votre fichier source.  
  
 **ID d’erreur :** BC30618  
  
### Pour corriger cette erreur  
  
-   Déplacez l’instruction `Namespace` en haut de votre déclaration d’espace de noms ou de votre fichier source.  
  
## Voir aussi  
 [Namespace Statement](../Topic/Namespace%20Statement.md)   
 [Espaces de noms dans Visual Basic](../Topic/Namespaces%20in%20Visual%20Basic.md)