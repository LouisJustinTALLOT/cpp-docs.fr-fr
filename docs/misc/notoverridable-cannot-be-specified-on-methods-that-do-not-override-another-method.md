---
title: "&#39;NotOverridable&#39; ne peut pas &#234;tre sp&#233;cifi&#233; sur les m&#233;thodes qui ne remplacent pas une autre m&#233;thode | Microsoft Docs"
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
  - "vbc31088"
  - "bc31088"
helpviewer_keywords: 
  - "BC31088"
ms.assetid: 0241197c-51fa-48b8-9a2a-4205d25641d3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;NotOverridable&#39; ne peut pas &#234;tre sp&#233;cifi&#233; sur les m&#233;thodes qui ne remplacent pas une autre m&#233;thode
Les propriétés et les méthodes sont `NotOverridable` par défaut. Le modificateur `NotOverridable` ne peut être utilisé que sur les méthodes qui remplacent une autre propriété ou méthode.  
  
 **ID d’erreur :** BC31088  
  
### Pour corriger cette erreur  
  
-   Supprimez le modificateur `NotOverridable` des propriétés et méthodes qui ne remplacent pas un autre membre.  
  
## Voir aussi  
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)   
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [NotOverridable](../Topic/NotOverridable%20\(Visual%20Basic\).md)   
 [Overridable](../Topic/Overridable%20\(Visual%20Basic\).md)