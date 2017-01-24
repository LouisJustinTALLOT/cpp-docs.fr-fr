---
title: "Erreur du compilateur CS0818 | Microsoft Docs"
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
  - "CS0818"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0818"
ms.assetid: e4941018-a10a-4636-98ea-aade29e45728
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0818
Les variables locales implicitement typées doivent être initialisées  
  
 Une variable locale implicitement typée doit être initialisée avec une valeur au moment même où elle est déclarée.  
  
### Pour corriger cette erreur  
  
1.  Affectez une valeur à la variable ou attribuez\-lui un type explicite.  
  
## Exemple  
 Le code suivant génère l’erreur CS0818 :  
  
```  
// cs0818.cs class A { public static int Main() { var a; // CS0818 return -1; } }  
```  
  
## Voir aussi  
 [Variables locales implicitement typées](../Topic/Implicitly%20Typed%20Local%20Variables%20\(C%23%20Programming%20Guide\).md)