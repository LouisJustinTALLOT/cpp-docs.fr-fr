---
title: "&#39;MustInherit&#39; ne peut pas &#234;tre sp&#233;cifi&#233; pour le type partiel &#39;&lt;nom_type_partiel&gt;&#39;, car il ne peut pas &#234;tre combin&#233; avec &#39;NotInheritable&#39; sp&#233;cifi&#233; pour l’un de ses autres types partiels | Microsoft Docs"
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
  - "vbc30926"
  - "BC30926"
helpviewer_keywords: 
  - "BC30926"
ms.assetid: 59a0b5d9-f53c-4234-88f4-dfc66342f143
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MustInherit&#39; ne peut pas &#234;tre sp&#233;cifi&#233; pour le type partiel &#39;&lt;nom_type_partiel&gt;&#39;, car il ne peut pas &#234;tre combin&#233; avec &#39;NotInheritable&#39; sp&#233;cifi&#233; pour l’un de ses autres types partiels
Une classe est définie dans plusieurs déclarations partielles, dont une spécifie `MustInherit` et une autre `NotInheritable`.  
  
 Quand vous divisez la définition d’une classe en plusieurs déclarations partielles, le compilateur traite la classe comme l’union de toutes ses déclarations partielles. Cela s’applique non seulement aux membres, mais aussi à l’implémentation, à l’héritage et au niveau d’accès.  
  
 Une classe ne peut pas être *abstract* et *sealed*, c’est\-à\-dire qu’elle ne peut pas à la fois exiger et interdire l’héritage. Par conséquent, vous ne pouvez pas spécifier `MustInherit` et `NotInheritable` pour la même classe.  
  
 **ID d’erreur :** BC30926  
  
### Pour corriger cette erreur  
  
-   Choisissez si la classe doit exiger l’héritage, interdire l’héritage, ou ni l’un ni l’autre, et supprimez les mots clés qui sont inappropriés par rapport à votre choix.  
  
## Voir aussi  
 [Partial](../Topic/Partial%20\(Visual%20Basic\).md)   
 [MustInherit](../Topic/MustInherit%20\(Visual%20Basic\).md)   
 [NotInheritable](../Topic/NotInheritable%20\(Visual%20Basic\).md)   
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)