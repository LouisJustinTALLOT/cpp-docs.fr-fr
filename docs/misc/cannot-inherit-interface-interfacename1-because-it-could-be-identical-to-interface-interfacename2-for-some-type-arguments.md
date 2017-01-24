---
title: "Impossible d’h&#233;riter de l’interface &#39;&lt;nom_interface1&gt;&#39;, car elle peut &#234;tre identique &#224; l’interface &#39;&lt;nom_interface2&gt;&#39; pour certains arguments de type | Microsoft Docs"
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
  - "vbc32120"
  - "bc32120"
helpviewer_keywords: 
  - "BC32120"
ms.assetid: c91f84a1-e61d-4b5f-8028-221e64ac044c
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’h&#233;riter de l’interface &#39;&lt;nom_interface1&gt;&#39;, car elle peut &#234;tre identique &#224; l’interface &#39;&lt;nom_interface2&gt;&#39; pour certains arguments de type
Une interface générique hérite plusieurs fois d’une autre interface générique, et deux des héritages peuvent entrer en conflit pour certaines valeurs d’arguments de type.  
  
 Les instructions suivantes peuvent générer cette erreur.  
  
 `Public Interface interfaceA(Of u)`  
  
 `End Interface`  
  
 `Public Interface derivedInterface(Of t1, t2)`  
  
 `Inherits interfaceA(Of t1), interfaceA(Of t2)`  
  
 `End Interface`  
  
 Si `derivedInterface` est construit ou implémenté en fournissant le même type à `t1` et `t2`, il doit hériter de deux versions de `interfaceA` avec des arguments de type identiques. Procéder ainsi est source d’ambiguïté quant à la version à laquelle accéder.  
  
 **ID d’erreur :** BC32120  
  
### Pour corriger cette erreur  
  
-   Modifiez l’un des arguments de type fournis à l’interface dérivée afin qu’il n’existe aucun conflit.  
  
     ou  
  
-   Supprimez de l’instruction `Inherits` l’une des interfaces qui provoquent le conflit potentiel d’héritage ou d’implémentation.  
  
## Voir aussi  
 [NOT IN BUILD : Vue d’ensemble des interfaces](http://msdn.microsoft.com/fr-fr/f96bb470-c1b8-4c73-89bc-6f536b798da1)   
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [Inheritance Basics](../Topic/Inheritance%20Basics%20\(Visual%20Basic\).md)   
 [Inherits Statement](../Topic/Inherits%20Statement.md)   
 [Types génériques Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)