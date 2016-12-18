---
title: "Erreur du compilateur CS1939 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1939"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1939"
ms.assetid: 9a7cdd48-3d45-473a-a799-c7771ef8158d
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1939
Impossible de passer la variable de portée 'name' en tant que paramètre out ou ref  
  
 Une variable de portée est une variable en lecture seule qui est introduite dans une expression de requête et qui sert d’identificateur pour chaque élément consécutif dans une séquence source. Étant donné qu’elle n’est pas du tout modifiable, il est inutile de la passer par `ref` ou `out`. Ainsi, les deux opérations ne sont pas valides.  
  
### Pour corriger cette erreur  
  
1.  Passez la variable de portée par valeur.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1939 :  
  
```  
// cs1939.cs using System.Linq; class Test { public static void F(ref int i) { } public static void Main() { var list = new int[] { 0, 1, 2, 3, 4, 5 }; var q = from x in list let k = x select Test.F(ref x); // CS1939 } }  
```