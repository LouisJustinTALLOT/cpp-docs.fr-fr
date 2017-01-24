---
title: "Erreur du compilateur CS1654 | Microsoft Docs"
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
  - "CS1654"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1654"
ms.assetid: 471c1298-1908-449d-b765-8dc3cd81a11d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1654
Impossible de modifier les membres de 'variable', car il s’agit d’un 'type\_variable\_lecture\_seule'  
  
 Cette erreur se produit quand vous tentez de modifier les membres d’une variable qui est en lecture seule, car elle figure dans une construction spéciale.  
  
 Ce problème se produit fréquemment dans les boucles [foreach](../Topic/foreach,%20in%20\(C%23%20Reference\).md). Modifier la valeur des éléments de la collection constitue une erreur de compilation. Par conséquent, vous ne pouvez pas apporter de modifications aux éléments qui sont des [types valeur](../Topic/Value%20Types%20\(C%23%20Reference\).md), notamment les [structs](../Topic/Structs%20\(C%23%20Programming%20Guide\).md). Dans une collection dont les éléments sont des [types référence](../Topic/Reference%20Types%20\(C%23%20Reference\).md), vous pouvez modifier les membres accessibles de chaque élément, mais toute tentative d’ajout, de suppression ou de remplacement d’éléments complets génère [Compiler Error CS1656](../Topic/Compiler%20Error%20CS1656.md).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1654, car `Book` est un `struct`. Pour corriger l’erreur, remplacez le `struct` par une [classe](../Topic/class%20\(C%23%20Reference\).md).  
  
```  
using System.Collections.Generic; using System.Text; namespace CS1654 { struct Book { public string Title; public string Author; public double Price; public Book(string t, string a, double p) { Title=t; Author=a; Price=p; } } class Program { List<Book> list; static void Main(string[] args) { //Use a collection initializer to initialize the list Program prog = new Program(); prog.list = new List<Book>(); prog.list.Add(new Book ("The C# Programming Language", "Hejlsberg, Wiltamuth, Golde", 29.95)); prog.list.Add(new Book ("The C++ Programming Language", "Stroustrup", 29.95)); prog.list.Add(new Book ("The C Programming Language", "Kernighan, Ritchie", 29.95)); foreach(Book b in prog.list) { //Compile error if Book is a struct //Make Book a class to modify its members b.Price +=9.95; // CS1654 } } } }  
  
```