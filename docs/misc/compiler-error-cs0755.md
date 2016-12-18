---
title: "Erreur du compilateur CS0755 | Microsoft Docs"
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
  - "CS0755"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0755"
ms.assetid: 80613029-a009-4bdf-b1c2-1eec1e60c7b4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0755
Soit les deux déclarations de méthode partielles sont des méthodes d’extension, soit aucune ne l’est  
  
 Une méthode partielle se compose d’une déclaration de définition \(signature\) et une déclaration d’implémentation facultative \(corps\). Si la déclaration de définition est une méthode d’extension, la déclaration d’implémentation, si celle\-ci est définie, doit également être une méthode d’extension. Si la méthode de définition n’est pas une méthode d’extension, l’implémentation ne doit pas l’être non plus.  
  
### Pour corriger cette erreur  
  
1.  Supprimez le modificateur `this` d’une des deux déclarations, ou ajoutez\-le à la déclaration qui n’en contient pas.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0755 :  
  
```  
// cs0755.cs public static partial class Ext { static partial void Part(this C c); //Extension method // Typically the implementing declaration is in a separate file. static partial void Part(C c) //CS0755 { } } public partial class C { public static int Main() { return 1; } }  
```  
  
## Voir aussi  
 [Méthodes d'extension](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)