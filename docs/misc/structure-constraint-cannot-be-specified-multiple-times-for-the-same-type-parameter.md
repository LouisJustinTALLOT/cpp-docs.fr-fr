---
title: "La contrainte &#39;Structure&#39; ne peut pas &#234;tre sp&#233;cifi&#233;e plusieurs fois pour le m&#234;me param&#232;tre de type | Microsoft Docs"
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
  - "bc32102"
  - "vbc32102"
helpviewer_keywords: 
  - "BC32102"
ms.assetid: f4ebd416-7fb9-4a24-a8df-e9ee7ccc2c76
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La contrainte &#39;Structure&#39; ne peut pas &#234;tre sp&#233;cifi&#233;e plusieurs fois pour le m&#234;me param&#232;tre de type
Une liste de contraintes comprend plusieurs fois la contrainte [Structure \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/263ce115-ac36-4c05-8cb7-0e0eead5c6d0).  
  
 Une liste de contraintes sur un paramètre de type peut spécifier que l’argument de type passé à ce paramètre de type doit être un type valeur \(avec la contrainte `Structure`\) ou un type référence \(avec la contrainte [Classe \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)\). Vous ne pouvez pas spécifier les deux contraintes sur le même paramètre de type et vous ne pouvez pas spécifier l’une des deux plusieurs fois.  
  
 ID d’erreur : BC32102  
  
### Pour corriger cette erreur  
  
-   Supprimez les mots clés `Structure` redondants. Un seul doit figurer dans la liste de contraintes.  
  
## Voir aussi  
 [Types génériques Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)