---
title: "Erreur du compilateur CS0020 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0020"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0020"
ms.assetid: 7a54db39-6530-4e34-aa17-a90f85223d08
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0020
Division par zéro constant  
  
 Une expression utilise une valeur littérale \(non variable\) égale à zéro dans le dénominateur d’une opération de division. La division par zéro n’est pas définie et n’est donc pas valide.  
  
 L’exemple suivant génère l’erreur CS0020 :  
  
```  
// CS0020.cs namespace x { public class b { public static void Main() { 1 / 0;   // CS0020 } } }  
```  
  
## Voir aussi  
 [Opérateurs](../Topic/Operators%20\(C%23%20Programming%20Guide\).md)