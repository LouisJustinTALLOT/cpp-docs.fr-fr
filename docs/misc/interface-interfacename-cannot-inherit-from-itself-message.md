---
title: "L’interface &#39;&lt;nom_interface&gt;&#39; ne peut pas h&#233;riter d’elle-m&#234;me&#160;: &lt;message&gt; | Microsoft Docs"
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
  - "vbc30296"
  - "BC30296"
helpviewer_keywords: 
  - "BC30296"
ms.assetid: a5bc1ae2-2083-4e26-b8a4-3c4dd951fd27
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’interface &#39;&lt;nom_interface&gt;&#39; ne peut pas h&#233;riter d’elle-m&#234;me&#160;: &lt;message&gt;
Une [Inherits Statement](../Topic/Inherits%20Statement.md) dans une définition d’interface spécifie sa propre interface.  
  
 Une interface peut hériter d’une autre interface, qui lui fournit tous les membres de l’interface dont elle hérite. Elle n’a donc pas à redéfinir ces membres. Une telle interface est appelée *interface dérivée*, et l’interface dont elle hérite est appelée *interface de base*.  
  
 Une interface ne peut pas hériter d’elle\-même, car elle possède déjà tous ses propres membres.  
  
 **ID d’erreur :** BC30296  
  
### Pour corriger cette erreur  
  
1.  Vérifiez l’orthographe du nom de l’interface dans l’instruction `Inherits`.  
  
2.  Si vous ne comptez pas hériter d’une autre interface, supprimez l’intégralité de l’instruction `Inherits`.  
  
3.  Examinez le message cité pour obtenir des suggestions.  
  
## Voir aussi  
 [NOT IN BUILD : Héritage en Visual Basic](http://msdn.microsoft.com/fr-fr/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Interfaces](../Topic/Interfaces%20\(Visual%20Basic\).md)