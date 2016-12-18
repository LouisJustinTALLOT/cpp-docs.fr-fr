---
title: "Erreur du compilateur CS1928 | Microsoft Docs"
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
  - "CS1928"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1928"
ms.assetid: bcc9dbef-ded5-4ddd-8c03-a9837cb6d165
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1928
'Type' ne contient pas de définition pour 'method' et la meilleure surcharge de la méthode d’extension 'method' contient des arguments non valides.  
  
 Cette erreur se produit quand le compilateur ne trouve aucun membre de classe portant le nom de la méthode que vous avez appelée. Il peut trouver une méthode d’extension portant ce nom, mais pas avec une signature qui correspond aux types passés avec votre appel de méthode.  
  
### Pour corriger cette erreur  
  
1.  Passez les types qui correspondent à une méthode de classe ou à une méthode d’extension existante.  
  
## Exemple  
 Le code suivant génère l’erreur CS1928 :  
  
```  
// cs1928.cs class Test { static void Main() { Test t = new Test(); t.M("hi"); // CS1928 } } static class Ext { public static void M(this Test t, int i) { } }  
```  
  
 Cette erreur est souvent accompagnée de l’erreur CS1503 : Argument 'n' : conversion impossible de 'typeA' en 'typeB'.  
  
## Voir aussi  
 [Méthodes d'extension](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)