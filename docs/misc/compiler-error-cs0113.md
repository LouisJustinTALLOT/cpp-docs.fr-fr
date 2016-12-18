---
title: "Erreur du compilateur CS0113 | Microsoft Docs"
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
  - "CS0113"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0113"
ms.assetid: 43c5c0b7-67c0-45c1-8363-21c844c094f3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0113
Un membre 'fonction' marqué comme override ne peut pas être marqué comme new ni virtual  
  
 Marquer une méthode avec les mots clés [new](../Topic/new%20\(C%23%20Reference\).md) et [override](../Topic/override%20\(C%23%20Reference\).md) sont des opérations qui s’excluent mutuellement.  
  
 L’exemple suivant génère l’erreur CS0113 :  
  
```  
// CS0113.cs namespace MyNamespace { abstract public class MyClass { public abstract void Foo(); } public class MyClass2 : MyClass { override new public void Foo()   // CS0113, remove new keyword { } public static int Main() { return 0; } } }  
```