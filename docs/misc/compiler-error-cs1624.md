---
title: "Erreur du compilateur CS1624 | Microsoft Docs"
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
  - "CS1624"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1624"
ms.assetid: af7d049d-27e2-4ce1-973c-5c2cb3e56a63
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1624
Le corps de 'accesseur' ne peut pas être un bloc itérateur, car 'type' n'est pas un type d’interface itérateur  
  
 Cette erreur se produit si un accesseur d’itérateur est utilisé, mais que le type de retour n’est pas l’un des types d’interface itérateur suivants : <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, <xref:System.Collections.Generic.IEnumerator%601>. Pour éviter cette erreur, utilisez l’un des types d’interface itérateur comme type de retour.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1624 :  
  
```  
// CS1624.cs using System; using System.Collections; class C { public int Iterator // Try this instead: // public IEnumerable Iterator { get  // CS1624 { yield return 1; } } }  
```