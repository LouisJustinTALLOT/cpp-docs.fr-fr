---
title: "L’interface &#39;nom_interface&#39; ne peut pas &#234;tre index&#233;e, car elle n’a pas de propri&#233;t&#233; par d&#233;faut | Microsoft Docs"
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
  - "bc30547"
  - "vbc30547"
helpviewer_keywords: 
  - "BC30547"
ms.assetid: d9d83868-5e81-4ec5-878e-2303489d8f2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’interface &#39;nom_interface&#39; ne peut pas &#234;tre index&#233;e, car elle n’a pas de propri&#233;t&#233; par d&#233;faut
Les expressions d’index doivent générer une valeur dont le type est un tableau, une valeur dont le type a un ensemble de propriétés par défaut surchargées, ou un ensemble de propriétés surchargées. Une interface ne peut avoir qu’une seule méthode ou propriété par défaut. Cela signifie qu’elle peut hériter d’une interface contenant une propriété ou une méthode par défaut, ou que son bloc de définition peut contenir une méthode ou propriété marquée comme valeur par défaut.  
  
 **ID d’erreur :** BC30547  
  
### Pour corriger cette erreur  
  
-   Fournissez une propriété par défaut dans l’interface.  
  
## Voir aussi  
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)