---
title: "La classe &#39;&lt;nom_classe&gt;&#39; ne peut pas h&#233;riter d’elle-m&#234;me&#160;: &lt;message&gt; | Microsoft Docs"
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
  - "vbc30257"
  - "bc30257"
helpviewer_keywords: 
  - "BC30257"
ms.assetid: 03e3034c-a0fa-4619-84b9-5bc9aa0dfe80
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La classe &#39;&lt;nom_classe&gt;&#39; ne peut pas h&#233;riter d’elle-m&#234;me&#160;: &lt;message&gt;
Une instruction Inherits \([Inherits Statement](../Topic/Inherits%20Statement.md)\) dans une définition de classe spécifie sa propre classe.  
  
 Une classe peut hériter d’une autre classe, qui lui fournit tous les membres de la classe dont elle hérite. Par conséquent, elle n’a pas à redéfinir ces membres. Une telle classe est appelée *classe dérivée*, et la classe dont elle hérite est appelée *classe de base*.  
  
 Cela n’a pas de sens qu’une classe hérite d’elle\-même, parce qu’elle a déjà tous ses propres membres.  
  
 **ID d’erreur :** BC30257  
  
### Pour corriger cette erreur  
  
1.  Vérifiez l’orthographe du nom de la classe dans l’instruction `Inherits`.  
  
2.  Si vous ne comptez pas hériter d’une autre classe, supprimez l’intégralité de l’instruction `Inherits`.  
  
3.  Examinez le message cité pour obtenir des suggestions.  
  
## Voir aussi  
 [NOT IN BUILD : Héritage en Visual Basic](http://msdn.microsoft.com/fr-fr/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [NOT IN BUILD : Présentation des classes](http://msdn.microsoft.com/fr-fr/cc2355a2-cb98-4353-9440-736585aec46c)