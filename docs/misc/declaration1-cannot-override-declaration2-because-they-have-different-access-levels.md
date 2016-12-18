---
title: "&#39;&lt;d&#233;claration1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;d&#233;claration2&gt;&#39;, car elles ont des niveaux d’acc&#232;s diff&#233;rents | Microsoft Docs"
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
  - "bc30266"
  - "vbc30266"
helpviewer_keywords: 
  - "BC30266"
ms.assetid: c9c5c14e-876c-430d-ab98-5087c19efae7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;d&#233;claration1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;d&#233;claration2&gt;&#39;, car elles ont des niveaux d’acc&#232;s diff&#233;rents
Une déclaration de procédure ou de propriété tente de se substituer à un élément hérité du même nom, mais elle spécifie une autre accessibilité que celle de l’élément hérité. L’accessibilité de l’élément hérité, comme `Public` ou `Private`, doit être conservé lors de la substitution.  
  
 **ID d’erreur :** BC30266  
  
### Pour corriger cette erreur  
  
-   Modifiez l’accessibilité de l’élément de substitution pour qu’il corresponde à celle de l’élément hérité.  
  
## Voir aussi  
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Access Levels in Visual Basic](../Topic/Access%20Levels%20in%20Visual%20Basic.md)