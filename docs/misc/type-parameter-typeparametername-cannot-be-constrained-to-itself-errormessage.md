---
title: "Le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; ne peut pas &#234;tre limit&#233; par lui-m&#234;me&#160;: &#39;&lt;message_erreur&gt;&#39; | Microsoft Docs"
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
  - "bc32113"
  - "vbc32113"
helpviewer_keywords: 
  - "BC32113"
ms.assetid: a74128ae-11d0-46bf-8c0b-c7a2bf881d17
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; ne peut pas &#234;tre limit&#233; par lui-m&#234;me&#160;: &#39;&lt;message_erreur&gt;&#39;
Une liste de contraintes d’un paramètre de type contient ce même paramètre de type.  
  
 Une liste de contraintes appliquée à un paramètre de type peut spécifier autant d’interfaces que souhaité, mais ne peut spécifier qu’une seule classe. Un argument de type fourni pour ce paramètre de type doit implémenter chaque interface spécifiée et hériter de la classe spécifiée. Le compilateur nécessite des interfaces et des classes qui sont déjà définies quand il rencontre une liste de contraintes. Un paramètre de type n’est pas considéré comme un type défini tant qu’il n’est pas remplacé par un argument de type approprié fourni par le code qui crée le type générique.  
  
 **ID d’erreur :** BC32113  
  
### Pour corriger cette erreur  
  
1.  Vérifiez l’orthographe du paramètre de type et des contraintes de sa liste de contraintes.  
  
2.  Si tout est bien orthographié, supprimez le nom du paramètre de type de sa liste de contraintes. En effet, il ne peut pas être contraint par lui\-même.  
  
## Voir aussi  
 [Types génériques Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)