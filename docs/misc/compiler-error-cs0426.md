---
title: "Erreur du compilateur CS0426 | Microsoft Docs"
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
  - "CS0426"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0426"
ms.assetid: 62df0deb-3624-436e-9691-ebe3ee1fc31f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0426
Le nom de type 'identificateur' n’existe pas dans le type 'type'  
  
 Cette erreur se produit lorsque vous faites référence à un type imbriqué dans un autre type, mais que ce type imbriqué n’existe pas. Cela peut se produire si vous orthographiez mal le nom du type imbriqué. Vérifiez l’orthographe des noms utilisés et vérifiez que le type englobant comporte le membre attendu.  
  
 L’exemple suivant génère l’erreur CS0426 car la classe C n’a aucun type imbriqué A :  
  
```  
// CS0426.cs class C { // No nested types are declared. } class D { public static void Main() { C c = new C(); // Attempt to reference a nested type A: C.A a; // CS0426 because no such type C.A } }  
```  
  
## Voir aussi  
 [Classes et structs](../Topic/Classes%20and%20Structs%20\(C%23%20Programming%20Guide\).md)