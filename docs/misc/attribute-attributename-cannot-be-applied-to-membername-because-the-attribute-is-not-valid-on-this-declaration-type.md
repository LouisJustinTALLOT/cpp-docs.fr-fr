---
title: "L’attribut &#39;&lt;nom_attribut&gt;&#39; ne peut pas &#234;tre appliqu&#233; &#224; &#39;&lt;nom_membre&gt;&#39;, car il n’est pas valide dans ce type de d&#233;claration | Microsoft Docs"
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
  - "vbc30662"
  - "bc30662"
helpviewer_keywords: 
  - "BC30662"
ms.assetid: 5cd07950-37d0-45e9-8770-3eaac54ff7d9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’attribut &#39;&lt;nom_attribut&gt;&#39; ne peut pas &#234;tre appliqu&#233; &#224; &#39;&lt;nom_membre&gt;&#39;, car il n’est pas valide dans ce type de d&#233;claration
L’attribut utilisé n’est pas approprié à l’élément utilisé.  
  
 **ID d’erreur :** BC30662  
  
### Pour corriger cette erreur  
  
1.  Choisissez un attribut conçu pour l’élément utilisé. Par exemple, si vous utilisez une méthode, choisissez un attribut conçu pour être utilisé avec des méthodes.  
  
2.  Si vous utilisez des attributs personnalisés que vous avez développés, changez l’attribut `AttributeUsage` afin qu’il corresponde au type d’élément utilisé.  
  
## Voir aussi  
 <xref:System.AttributeUsageAttribute>   
 [NOT IN BUILD : Attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [NOT IN BUILD : Attributs personnalisés en Visual Basic](http://msdn.microsoft.com/fr-fr/d72d8a5c-8f64-4614-b15b-cad66845d047)