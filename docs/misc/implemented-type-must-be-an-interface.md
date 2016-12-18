---
title: "Le type impl&#233;ment&#233; doit &#234;tre une interface. | Microsoft Docs"
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
  - "bc30232"
  - "vbc30232"
helpviewer_keywords: 
  - "BC30232"
ms.assetid: 63f3dd4c-2f99-4070-b506-2fa808df24d4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type impl&#233;ment&#233; doit &#234;tre une interface.
Une instruction `Implements` ne spécifie pas une interface. Une classe ne peut implémenter qu’une interface.  
  
 **ID d’erreur :** BC30232  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que le nom de l’interface est correctement orthographié.  
  
2.  Si l’instruction spécifie une classe, utilisez l’instruction `Inherits`.  
  
## Voir aussi  
 [Implements Statement](../Topic/Implements%20Statement.md)   
 [Inherits Statement](../Topic/Inherits%20Statement.md)   
 [NOT IN BUILD : Héritage en Visual Basic](http://msdn.microsoft.com/fr-fr/e5e6e240-ed31-4657-820c-079b7c79313c)