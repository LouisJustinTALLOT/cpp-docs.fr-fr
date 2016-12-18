---
title: "Erreur du compilateur CS1620 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1620"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1620"
ms.assetid: 13933976-218a-4fe2-8fde-5b9af522e2e5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1620
L’argument 'nombre' doit être passé avec le mot clé 'mot\_clé'  
  
 Cette erreur se produit si vous passez un argument à une fonction qui accepte un paramètre [ref](../Topic/ref%20\(C%23%20Reference\).md) ou [out](../Topic/out%20\(C%23%20Reference\).md) et que vous n’incluez pas le mot clé `ref` ou `out` au point d’appel, ou que vous incluez le mot clé incorrect. Le texte d’erreur indique le mot clé approprié à utiliser et l’argument qui a provoqué l’échec.  
  
 L’exemple suivant génère l’avertissement CS1620 :  
  
```  
// CS1620.cs class C { void f(ref int i) {} public static void Main() { int x = 1; f(out x);  // CS1620 – f takes a ref parameter, not an out parameter // Try this line instead: // f(ref x); } }  
```