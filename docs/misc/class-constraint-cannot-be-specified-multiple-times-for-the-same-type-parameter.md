---
title: "La contrainte &#39;Class&#39; ne peut pas &#234;tre sp&#233;cifi&#233;e plusieurs fois pour le m&#234;me param&#232;tre de type | Microsoft Docs"
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
  - "bc32101"
  - "vbc32101"
helpviewer_keywords: 
  - "BC32101"
ms.assetid: fac2330a-e397-4bd9-8166-934407575f9e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La contrainte &#39;Class&#39; ne peut pas &#234;tre sp&#233;cifi&#233;e plusieurs fois pour le m&#234;me param&#232;tre de type
Une liste de contraintes inclut plusieurs fois la contrainte [Class \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/0777c6e6-46bc-451b-ad70-57b49d4ef4f7).  
  
 Une liste de contraintes sur un paramètre de type peut spécifier que l’argument de type passé à ce paramètre de type doit être un type valeur \(avec la contrainte [Structure \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)\) ou un type référence \(avec la contrainte `Class`\). Vous ne pouvez pas spécifier les deux contraintes sur le même paramètre de type et vous ne pouvez pas spécifier l’une ou l’autre plusieurs fois.  
  
 ID d’erreur : BC32101  
  
### Pour corriger cette erreur  
  
-   Supprimez les mots clés `Class` redondants. La liste de contraintes ne doit en avoir qu’un.  
  
## Voir aussi  
 [Types génériques Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)