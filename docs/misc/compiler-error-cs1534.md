---
title: "Erreur du compilateur CS1534 | Microsoft Docs"
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
  - "CS1534"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1534"
ms.assetid: afb28c3a-a74c-4e47-b016-9e3245a5a1b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1534
L’opérateur binaire surchargé 'opérateur' accepte deux paramètres  
  
 La définition d’un [opérateur surchargeable](../Topic/Overloadable%20Operators%20\(C%23%20Programming%20Guide\).md) binaire doit prendre deux paramètres.  
  
 L’exemple suivant génère l’erreur CS1534 :  
  
```  
// CS1534.cs class MyClass { public static MyClass operator - (MyClass MC1, MyClass MC2, MyClass MC3)   // CS1534 // try the following line instead // public static MyClass operator - (MyClass MC1, MyClass MC2) { return new MyClass(); } public static int Main() { return 1; } }  
```