---
title: "&#39;&lt;type1&gt;&#39; ne peut pas remplacer &lt;type2&gt;, car il n’est pas d&#233;clar&#233; &#39;Overridable&#39; | Microsoft Docs"
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
  - "bc31086"
  - "vbc31086"
helpviewer_keywords: 
  - "BC31086"
ms.assetid: ce071994-2e32-4460-a65d-f48f914386c6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;type1&gt;&#39; ne peut pas remplacer &lt;type2&gt;, car il n’est pas d&#233;clar&#233; &#39;Overridable&#39;
Un membre dans une classe dérivée substitue un membre de classe de base qui n’est pas marqué avec le modificateur `Overridable`.  
  
 **ID d’erreur :** BC31086  
  
### Pour corriger cette erreur  
  
1.  Ajoutez le modificateur `Overridable` au membre substitué dans la classe de base.  
  
2.  Utilisez le mot clé `Shadows` pour masquer l’élément dans la classe de base.  
  
## Voir aussi  
 [Overridable](../Topic/Overridable%20\(Visual%20Basic\).md)   
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)   
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)