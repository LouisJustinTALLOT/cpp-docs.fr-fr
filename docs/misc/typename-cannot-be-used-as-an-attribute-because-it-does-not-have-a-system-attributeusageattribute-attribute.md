---
title: "&#39;&lt;nom_type&gt;&#39; ne peut pas &#234;tre utilis&#233; en tant qu’attribut, car il n’a pas un attribut &#39;System.AttributeUsageAttribute&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31505"
  - "bc31505"
helpviewer_keywords: 
  - "BC31505"
ms.assetid: 7dd84c9d-6711-4dab-afc6-1fe4dee78051
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_type&gt;&#39; ne peut pas &#234;tre utilis&#233; en tant qu’attribut, car il n’a pas un attribut &#39;System.AttributeUsageAttribute&#39;
L’utilisateur a tenté d’utiliser un attribut déclaré sans `System.AttributeUsageAttribute` pour définir son utilisation.  
  
 **ID d’erreur :** BC31505  
  
### Pour corriger cette erreur  
  
1.  Les attributs personnalisés doivent être des classes dérivées de`System.Attribute` auxquelles l’attribut `AttributeUsageAttribute` est appliqué.  
  
## Voir aussi  
 <xref:System.AttributeUsageAttribute>   
 [NOT IN BUILD : Attributs personnalisés en Visual Basic](http://msdn.microsoft.com/fr-fr/d72d8a5c-8f64-4614-b15b-cad66845d047)