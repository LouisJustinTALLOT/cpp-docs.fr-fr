---
title: "Erreur du compilateur CS0622 | Microsoft Docs"
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
  - "CS0622"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0622"
ms.assetid: aef77a69-d8b7-41f8-9539-258deaef5cc4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0622
Les expressions d’initialiseur de tableau ne peuvent être utilisées que pour assigner des types tableau. Essayez plutôt d’utiliser une expression new.  
  
 La syntaxe permettant d’initialiser un tableau a été utilisée dans la déclaration d’un non\-tableau.  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS0622 :  
  
```  
// CS0622.cs using System; public class Test { public static void Main () { Test t = { new Test() };   // CS0622 // Try the following instead: // Test[] t = { new Test() }; } }  
```