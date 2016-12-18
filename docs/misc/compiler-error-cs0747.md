---
title: "Erreur du compilateur CS0747 | Microsoft Docs"
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
  - "CS0747"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0747"
ms.assetid: dc1b7e38-cee5-406c-b193-a60ec4faebe1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0747
Déclarateur de membre initialiseur non valide  
  
 Un initialiseur d’objet est utilisé pour assigner des valeurs à des propriétés ou des champs. Les expressions qui ne sont pas des assignations à une propriété ou à un champ provoquent une erreur de compilation.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que toutes les expressions de l’initialiseur sont des assignations aux propriétés ou aux champs du type. Dans l’exemple suivant, la deuxième expression correspond à une erreur, car la valeur `1` n’est pas assignée à une propriété ou à un champ de `List<int>`.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0747 :  
  
```  
// cs0747.cs using System.Collections.Generic; public class C { public static int Main() { var t = new List<int> { Capacity = 2, 1 }; // CS0747 return 1; } }  
```  
  
## Voir aussi  
 [Initialiseurs d'objets et de collections](../Topic/Object%20and%20Collection%20Initializers%20\(C%23%20Programming%20Guide\).md)