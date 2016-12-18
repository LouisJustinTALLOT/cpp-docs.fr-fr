---
title: "&#39;System.Void&#39; ne peut &#234;tre utilis&#233; que dans une expression GetType | Microsoft Docs"
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
  - "bc31422"
  - "vbc31422"
helpviewer_keywords: 
  - "BC31422"
ms.assetid: 84e45194-cb46-41f6-8420-a1498baeaaba
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Void&#39; ne peut &#234;tre utilis&#233; que dans une expression GetType
Une expression dans une instruction d’assignation ou une déclaration utilise <xref:System.Void> comme type de variable, de paramètre de procédure, de retour de fonction ou d’argument de type.  
  
 La structure <xref:System.Void> est un type spécialisé utilisé en interne par le .NET Framework et en particulier par Visual C\# et Visual C\+\+. Elle représente un type valeur de retour pour une méthode qui ne retourne pas de valeur. Visual Basic utilise une procédure `Sub` quand aucune valeur n’est retournée et une procédure `Function` quand une valeur est retournée.  
  
 Vous pouvez tester une variable référence à l’aide de l’opérateur [GetType Operator](../Topic/GetType%20Operator%20\(Visual%20Basic\).md) pour déterminer si son type d’exécution a la valeur <xref:System.Void>, mais vous ne pouvez pas utiliser <xref:System.Void> dans un autre contexte.  
  
 **ID d’erreur :** BC31422  
  
### Pour corriger cette erreur  
  
1.  Si vous souhaitez comparer le type d’exécution d’une variable à <xref:System.Void>, utilisez l’opérateur `GetType`.  
  
2.  À moins que vous n’ayez une raison particulière de comparer un type d’exécution à <xref:System.Void>, supprimez entièrement la référence à ce type.  
  
## Voir aussi  
 <xref:System.Void>   
 [GetType Operator](../Topic/GetType%20Operator%20\(Visual%20Basic\).md)