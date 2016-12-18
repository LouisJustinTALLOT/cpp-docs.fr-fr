---
title: "Erreur du compilateur CS1059 | Microsoft Docs"
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
  - "CS1059"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1059"
ms.assetid: 3ebd02ab-e40d-4aad-b901-a0cb6e2eace7
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1059
L’opérande d’un opérateur d’incrémentation ou de décrémentation doit être une variable, une propriété ou un indexeur.  
  
 Cette erreur est générée quand vous tentez d’incrémenter ou de décrémenter une valeur constante. Elle peut également se produire si vous tentez d’incrémenter une expression telle que `(a+b)++`.  
  
### Pour corriger cette erreur  
  
-   Rendez la variable non constante.  
  
-   Supprimez l’opérateur d’incrémentation ou de décrémentation.  
  
-   Stockez l’expression dans une variable, puis incrémentez la variable.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1059, car `i` est une constante, et non une variable, et `E` est un type `Enum`, dont les éléments sont également des valeurs constantes.  
  
```  
// CS1059.cs class Program { public enum E : sbyte { a = 1, b = 2 } static void Main(string[] args) { const int i = 0; i++;            // CS1059 E test = E.a++; // CS1059 } }  
```  
  
## Voir aussi  
 [Constantes](../Topic/Constants%20\(C%23%20Programming%20Guide\).md)