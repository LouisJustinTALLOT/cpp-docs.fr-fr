---
title: "&#39;&lt;sp&#233;cificateur&gt;&#39; n’est pas valide dans une d&#233;claration de m&#233;thode d’interface. | Microsoft Docs"
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
  - "bc30270"
  - "vbc30270"
helpviewer_keywords: 
  - "BC30270"
ms.assetid: 598f2944-3e5d-4686-b6f7-2b4bcaf5c211
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;sp&#233;cificateur&gt;&#39; n’est pas valide dans une d&#233;claration de m&#233;thode d’interface.
Une instruction `Function` ou `Sub` à l’intérieur d’une interface contient un mot clé non valide, comme `Implements`. Une interface peut seulement définir des membres, elle ne peut pas les implémenter.  
  
 **ID d’erreur :** BC30270  
  
### Pour corriger cette erreur  
  
1.  Supprimez le mot clé non valide de l’instruction de déclaration.  
  
2.  Déplacez l’implémentation des membres d’interface vers une classe qui implémente l’interface.  
  
## Voir aussi  
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [Implements Statement](../Topic/Implements%20Statement.md)