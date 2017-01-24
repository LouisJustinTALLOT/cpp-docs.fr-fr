---
title: "Le commentaire XML ne peut pas &#234;tre appliqu&#233; plusieurs fois sur un &lt;type&gt; partiel | Microsoft Docs"
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
  - "bc42314"
  - "vbc42314"
helpviewer_keywords: 
  - "BC42314"
ms.assetid: 23c76238-843a-44fe-88b7-25e604ee924b
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le commentaire XML ne peut pas &#234;tre appliqu&#233; plusieurs fois sur un &lt;type&gt; partiel
Le commentaire XML ne peut pas être appliqué plusieurs fois sur un \<type\> partiel. Les commentaires XML pour ce \<type\> seront ignorés.  
  
 Un bloc de commentaires XML peut apparaître au\-dessus d’une seule partie d’un type partiel.  
  
 Si un bloc de commentaires XML apparaît au\-dessus de plusieurs parties d’un type partiel, cet avertissement est créé pour chaque bloc de commentaires, et le commentaire XML de niveau supérieur est ignoré.  
  
 **ID d’erreur :** BC42314  
  
### Pour corriger cette erreur  
  
-   Supprimez les blocs de commentaires superflus.  
  
## Voir aussi  
 [How to: Create XML Documentation](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [XML Comment Tags](../Topic/Recommended%20XML%20Tags%20for%20Documentation%20Comments%20\(Visual%20Basic\).md)