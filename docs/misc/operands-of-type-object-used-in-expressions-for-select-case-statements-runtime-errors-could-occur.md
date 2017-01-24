---
title: "Op&#233;randes de type Object utilis&#233;s dans les expressions pour les instructions &#39;Select&#39;, &#39;Case&#39;&#160;; des erreurs au moment de l’ex&#233;cution peuvent se produire | Microsoft Docs"
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
  - "vbc42036"
  - "bc42036"
helpviewer_keywords: 
  - "BC42036"
ms.assetid: f11e9c9f-aa66-4eb1-8f49-abf713bef885
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Op&#233;randes de type Object utilis&#233;s dans les expressions pour les instructions &#39;Select&#39;, &#39;Case&#39;&#160;; des erreurs au moment de l’ex&#233;cution peuvent se produire
Une construction `Select`...`Case` utilise une ou plusieurs expressions du [Object Data Type](../Topic/Object%20Data%20Type.md).  
  
 Quand une variable ou une expression prend la valeur `Object`, le compilateur doit exécuter une *liaison tardive*, ce qui entraîne des opérations supplémentaires au moment de l’exécution. Cela expose également votre application à de potentielles erreurs d’exécution. Par exemple, si vous assignez un <xref:System.Windows.Forms.Form> à une variable `Object` et que vous essayez de le comparer à un nombre, le runtime lève une <xref:System.InvalidCastException>, car Visual Basic ne peut pas convertir un objet <xref:System.Windows.Forms.Form> en une valeur numérique.  
  
 Les expressions d’une construction `Select`...`Case` doivent être toutes du même type de données ou étroitement liées à des types de données mutuellement convertibles. Il en est ainsi parce que chaque instruction `Case` compare au moins une valeur par rapport à l’expression test dont dépend la construction `Select`...`Case`.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **ID d’erreur :** BC42036  
  
### Pour corriger cette erreur  
  
-   Si possible, réorganisez toutes les expressions afin qu’elles aient pour valeurs des types de données pour lesquels les opérateurs de comparaison sont définis.  
  
## Voir aussi  
 [Select...Case Statement](../Topic/Select...Case%20Statement%20\(Visual%20Basic\).md)   
 [Arithmetic Operators in Visual Basic](../Topic/Arithmetic%20Operators%20in%20Visual%20Basic.md)   
 [Comparison Operators in Visual Basic](../Topic/Comparison%20Operators%20in%20Visual%20Basic.md)