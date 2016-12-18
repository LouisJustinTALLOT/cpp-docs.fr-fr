---
title: "Erreur du compilateur CS0239 | Microsoft Docs"
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
  - "CS0239"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0239"
ms.assetid: 2e07bbc2-03a9-44b2-b321-477ca95fff8c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0239
'member' : impossible de substituer le membre hérité 'inherited member', car il est sealed  
  
 Un membre ne peut pas se [substituer](../Topic/override%20\(C%23%20Reference\).md) à un membre hérité [sealed](../Topic/sealed%20\(C%23%20Reference\).md). Pour plus d'informations, consultez [Checked et unchecked](../Topic/Checked%20and%20Unchecked%20\(C%23%20Reference\).md).  
  
 L’exemple suivant génère l’erreur CS0239 :  
  
```  
// CS0239.cs abstract class MyClass { public abstract void f(); } class MyClass2 : MyClass { public static void Main() { } public override sealed void f() { } } class MyClass3 : MyClass2 { public override void f()   // CS0239 // Try the following definition instead: // public new void f() { } }  
```