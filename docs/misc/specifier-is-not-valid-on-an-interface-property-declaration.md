---
title: "&#39;&lt;sp&#233;cificateur&gt;&#39; n’est pas valide dans une d&#233;claration de propri&#233;t&#233; d’interface | Microsoft Docs"
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
  - "vbc30273"
  - "bc30273"
helpviewer_keywords: 
  - "BC30273"
ms.assetid: f10c4f5f-6176-4dba-99a9-b58f3b390fba
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;sp&#233;cificateur&gt;&#39; n’est pas valide dans une d&#233;claration de propri&#233;t&#233; d’interface
Une instruction `Property` à l’intérieur d’une interface contient un mot clé non valide, comme `Implements`. Une interface peut seulement définir des membres, elle ne peut pas les implémenter.  
  
 **ID d’erreur :** BC30273  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé non valide de l’instruction de déclaration.  
  
-   Déplacez l’implémentation des membres d’interface vers une classe qui implémente l’interface.  
  
## Voir aussi  
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [Implements Statement](../Topic/Implements%20Statement.md)