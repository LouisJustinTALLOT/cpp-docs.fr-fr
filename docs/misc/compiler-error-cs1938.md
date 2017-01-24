---
title: "Erreur du compilateur CS1938 | Microsoft Docs"
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
  - "CS1938"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1938"
ms.assetid: fc8de996-f7a1-46e8-b07b-aea520b391b9
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1938
Le nom 'name' n’est pas dans la portée à droite de 'equals'. Échangez les expressions de chaque côté de 'equals'.  
  
 Le mot clé `equals` est un opérateur spécial utilisé dans une clause `join` pour déterminer l’égalité entre deux expressions. La variable de portée pour la séquence source côté gauche est dans la portée à gauche du signe égal, et la variable de portée pour la source côté droite est uniquement dans la portée à gauche du signe égal. Pour vérifier ceci, testez IntelliSense dans l’exemple de code suivant.  
  
### Pour corriger cette erreur  
  
1.  Permutez les deux variables de portée, comme indiqué dans la ligne commentée de l’exemple suivant :  
  
## Exemple  
 Le code suivant génère l’erreur CS1938 :  
  
```  
// cs1938.cs using System.Linq; class Test { static void Main() { int[] sourceA = { 1, 2, 3, 4, 5 }; int[] sourceB = { 3, 4, 5, 6, 7 }; var query = from a in sourceA join b in sourceB on b equals a // CS1938 // Try the following line instead. // join b in sourceB on a equals b select new { a, b }; } }  
```  
  
## Voir aussi  
 [join, clause](../Topic/join%20clause%20\(C%23%20Reference\).md)