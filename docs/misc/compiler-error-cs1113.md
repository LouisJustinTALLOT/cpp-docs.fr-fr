---
title: "Erreur du compilateur CS1113 | Microsoft Docs"
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
  - "CS1113"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1113"
ms.assetid: ef2d828f-b5ee-4be9-ba2e-36df5502cc5a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1113
Impossible d’utiliser les méthodes d’extension 'name' définies sur le type valeur 'name' pour créer des délégués.  
  
 Les méthodes d’extension définies pour les types de classes peuvent être utilisées pour créer des délégués. Celles qui sont définies pour les types valeur ne peuvent pas être utilisées.  
  
### Pour corriger cette erreur  
  
1.  Associez la méthode d’extension à un type de classe.  
  
2.  Définissez la méthode comme une méthode normale sur la structure.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1113 :  
  
```  
// cs1113.cs using System; public static class Extensions { public static S ExtMethod(this S s) { return s; } } public struct S { } public class Test { static int Main() { Func<S> f = new S().ExtMethod; // CS1113 return 1; } }  
  
```  
  
## Voir aussi  
 [Méthodes d'extension](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)