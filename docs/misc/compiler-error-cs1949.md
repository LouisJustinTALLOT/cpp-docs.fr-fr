---
title: "Erreur du compilateur CS1949 | Microsoft Docs"
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
  - "CS1949"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1949"
ms.assetid: 959f553e-ac3d-43a1-b0a0-11e270f2ad64
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1949
Le mot clé contextuel 'var' ne peut pas être utilisé dans une déclaration de variable de portée.  
  
 Une variable de portée est implicitement typée par le compilateur. Il est inutile d’utiliser [var](../Topic/var%20\(C%23%20Reference\).md) avec une variable de portée.  
  
### Pour corriger cette erreur  
  
1.  Supprimez le mot clé `var`  situé devant la variable de portée.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1949 :  
  
```  
// cs1949.cs using System; using System.Linq; class Test { static void Main() { var x = from var i in Enumerable.Range(1, 100) // CS1949 select i; } }  
```  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](../Topic/LINQ%20Query%20Expressions%20\(C%23%20Programming%20Guide\).md)   
 [Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md)