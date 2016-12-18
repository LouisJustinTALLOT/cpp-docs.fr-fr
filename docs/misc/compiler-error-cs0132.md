---
title: "Erreur du compilateur CS0132 | Microsoft Docs"
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
  - "CS0132"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0132"
ms.assetid: e8ad1281-2912-4b6a-b2af-a319a23ddd16
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0132
'constructeur' : un constructeur statique ne doit pas avoir de paramètres  
  
 Un constructeur [static](../Topic/static%20\(C%23%20Reference\).md) ne peut pas être déclaré avec un ou plusieurs paramètres. Pour plus d'informations, consultez [Constructeurs](../Topic/Constructors%20\(C%23%20Programming%20Guide\).md).  
  
 L’exemple suivant génère l’erreur CS0132 :  
  
```  
// CS0132.cs namespace MyNamespace { public class MyClass { public MyClass(int i) { } } public class MyClass2 : MyClass { static MyClass2(int i)   // CS0132 { } } }  
```