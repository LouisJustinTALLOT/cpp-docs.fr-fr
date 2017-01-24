---
title: "Les types Nullable ne sont pas autoris&#233;s dans les expressions de compilation conditionnelles | Microsoft Docs"
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
  - "bc33111"
  - "vbc33111"
helpviewer_keywords: 
  - "BC33111"
ms.assetid: 2c2587e5-2179-4a31-bcf7-7004db6f2d73
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les types Nullable ne sont pas autoris&#233;s dans les expressions de compilation conditionnelles
Un type Nullable ne peut pas être utilisé dans l’expression d’une directive de compilation conditionnelle. Par exemple, le code suivant génère cette erreur.  
  
```vb#  
'#Const triggerPoint = 0 '' Not valid. '#If CType(triggerpoint, Boolean?) = True Then '        ' Body of the conditional directive. '#End If  
```  
  
 **ID d’erreur :** BC33111  
  
### Pour corriger cette erreur  
  
-   Supprimer la désignation de type Nullable.  
  
## Voir aussi  
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)   
 [\#If...Then...\#Else Directives](../Topic/%23If...Then...%23Else%20Directives.md)   
 [Conditional Compilation](../Topic/Conditional%20Compilation%20in%20Visual%20Basic.md)