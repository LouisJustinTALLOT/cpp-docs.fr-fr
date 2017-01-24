---
title: "Erreur du compilateur CS1525 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1525"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1525"
ms.assetid: 7913f589-2f2e-40bc-a27e-0b6930336484
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1525
Terme d’expression non valide 'caractère'  
  
 Le compilateur a détecté un caractère non valide dans une expression.  
  
 L’exemple suivant génère l’erreur CS1525 :  
  
```  
// CS1525.cs class x { public static void Main() { int i = 0; i = i +   // OK - identifier 'c' +     // OK - character (5) +     // OK - parenthesis [ +       // CS1525, operator not a valid expression element throw +   // CS1525, keyword not allowed in expression void;     // CS1525, void not allowed in expression } }  
```  
  
 Une étiquette vide peut également générer l’erreur CS1525, comme dans l’exemple suivant :  
  
```  
// CS1525b.cs using System; public class MyClass { public static void Main() { goto FoundIt; FoundIt:      // CS1525 // Uncomment the following line to resolve: // System.Console.Write("Hello"); } }  
```