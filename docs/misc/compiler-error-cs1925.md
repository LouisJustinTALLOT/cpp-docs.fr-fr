---
title: "Erreur du compilateur CS1925 | Microsoft Docs"
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
  - "CS1925"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1925"
ms.assetid: b60806a5-2ccf-47f5-873b-7ac2292fdb54
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1925
Impossible d’initialiser l’objet de type 'type' avec un initialiseur de collection.  
  
 Les initialiseurs de collection sont autorisés uniquement pour les classes de collection qui répondent à certains critères. Pour plus d'informations, consultez [Initialiseurs d'objets et de collections](../Topic/Object%20and%20Collection%20Initializers%20\(C%23%20Programming%20Guide\).md). Cette erreur est également générée lorsque vous essayez d’utiliser la forme abrégée d’un initialiseur de tableau imbriqué dans un initialiseur de collection.  
  
### Pour corriger cette erreur  
  
1.  Initialisez l’objet en appelant ses méthodes et ses constructeurs.  
  
## Exemple  
 Le code suivant génère l’erreur CS1925 :  
  
```  
// cs1925.cs public class Student { public int[] Scores; } class Test { static void Main(string[] args) { Student student = new Student { Scores = { 1, 2, 3 } }; // CS1925 } }  
```