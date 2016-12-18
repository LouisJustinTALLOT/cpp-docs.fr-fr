---
title: "&#39;Of&#39; requis lors de la sp&#233;cification des arguments de type pour un type ou une m&#233;thode g&#233;n&#233;rique | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32093"
  - "vbc32093"
helpviewer_keywords: 
  - "BC32093"
ms.assetid: 9a1baf12-a4a4-442d-9baa-852ad30a956b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Of&#39; requis lors de la sp&#233;cification des arguments de type pour un type ou une m&#233;thode g&#233;n&#233;rique
Une instruction essaie de construire un type à partir d’un type générique, ou d’appeler une méthode générique, sans utiliser de clause [Of](../Topic/Of%20Clause%20\(Visual%20Basic\).md).  
  
 La syntaxe [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] pour les types génériques exige que les paramètres et arguments de type soient introduits par le mot clé `Of`. De plus, la liste des paramètres ou arguments de type doit être mise entre parenthèses.  
  
 **ID d’erreur :** BC32093  
  
### Pour corriger cette erreur  
  
-   Incluez le mot clé `Of` au début de la liste d’arguments de type et mettez l’intégralité de la liste entre parenthèses.  
  
## Voir aussi  
 [Types génériques Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Comment : utiliser une classe générique](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)