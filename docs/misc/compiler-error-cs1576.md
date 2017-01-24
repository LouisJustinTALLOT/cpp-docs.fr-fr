---
title: "Erreur du compilateur CS1576 | Microsoft Docs"
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
  - "CS1576"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1576"
ms.assetid: 3e39cb80-e7de-4c78-a22a-57e267121a96
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1576
Le numéro de ligne spécifié pour la directive \#line est manquant ou non valide  
  
 Le compilateur a détecté une erreur concernant la valeur passée à la directive [\#line](../Topic/%23line%20\(C%23%20Reference\).md).  
  
 L’exemple suivant génère l’erreur CS1576 :  
  
```  
// CS1576.cs public class MyClass { static void Main() { #line "abc.sc"         // CS1576 // try the following line instead //#line  101 "abc.sc" intt i;  // error will be reported on line 101 } }  
```