---
title: "R&#233;f&#233;rence exig&#233;e &#224; l’assembly &#39;&lt;identit&#233;_assembly&gt;&#39; contenant le type &#39;&lt;nom_type&gt;&#39;, mais aucune r&#233;f&#233;rence appropri&#233;e n’a pu &#234;tre trouv&#233;e en raison d’&#233;ventuelles r&#233;f&#233;rences circulaires&#160;: &lt;liste_d&#233;pendance_r&#233;f&#233;rence&gt; | Microsoft Docs"
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
  - "bc30962"
  - "vbc30962"
helpviewer_keywords: 
  - "BC30962"
ms.assetid: 6f338158-bfb4-4cc0-bbf7-1111c708613c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# R&#233;f&#233;rence exig&#233;e &#224; l’assembly &#39;&lt;identit&#233;_assembly&gt;&#39; contenant le type &#39;&lt;nom_type&gt;&#39;, mais aucune r&#233;f&#233;rence appropri&#233;e n’a pu &#234;tre trouv&#233;e en raison d’&#233;ventuelles r&#233;f&#233;rences circulaires&#160;: &lt;liste_d&#233;pendance_r&#233;f&#233;rence&gt;
Une expression utilise un type, comme une classe, une structure, une interface, une énumération ou un délégué, qui est défini en dehors de votre projet. Toutefois, votre référence de projet à cet assembly fait partie d’un ensemble de références circulaires.  
  
 Quand plusieurs projets ont des références entre eux, ces références peuvent être *circulaires*. Par exemple, deux projets peuvent avoir des références l’un à l’autre. De manière plus générale, une chaîne de références d’un projet à l’autre peut finir par revenir au projet de départ. Dans ce cas, il n’existe aucun projet final à la fin de la chaîne avec lequel résoudre la référence.  
  
 Pour accéder à un type défini dans un autre assembly, le compilateur [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] doit avoir une référence à cet assembly. Cette référence doit être unique et non équivoque et elle ne doit pas provoquer de références circulaires entre les projets.  
  
 **ID d’erreur :** BC30962  
  
### Pour corriger cette erreur  
  
-   Dans vos propriétés de projet, ajoutez une référence directe au projet qui produit l’assembly qui définit le type que vous utilisez.  
  
## Voir aussi  
 [Gestion des références dans un projet](../Topic/Managing%20references%20in%20a%20project.md)   
 [NIB : Références aux espaces de noms et aux composants](http://msdn.microsoft.com/fr-fr/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NIB Comment : modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/fr-fr/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Dépannage de références rompues](../Topic/Troubleshooting%20Broken%20References.md)