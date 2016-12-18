---
title: "Erreur du compilateur CS0216 | Microsoft Docs"
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
  - "CS0216"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0216"
ms.assetid: afb3dd29-3eff-4b62-8267-eb726c2bcee4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0216
L’opérateur 'opérateur' exige qu’un opérateur correspondant 'opérateur\_manquant' soit aussi défini  
  
 Un opérateur [true](../Topic/true%20\(C%23%20Reference\).md) défini par l’utilisateur exige un opérateur [false](../Topic/false%20\(C%23%20Reference\).md) défini par l’utilisateur et vice versa. Pour plus d'informations, consultez [Opérateurs](../Topic/Operators%20\(C%23%20Programming%20Guide\).md).  
  
 L’exemple suivant génère l’erreur CS0216 :  
  
```  
// CS0216.cs class MyClass { public static bool operator true (MyClass MyInt)   // CS0216 { return true; } // to resolve, uncomment the following operator definition /* public static bool operator false (MyClass MyInt) { return true; } */ public static void Main() { } }  
```