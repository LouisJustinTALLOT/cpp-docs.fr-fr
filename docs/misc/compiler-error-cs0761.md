---
title: "Erreur du compilateur CS0761 | Microsoft Docs"
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
  - "CS0761"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0761"
ms.assetid: b16ac1df-0ddc-44d2-89f1-8d9c32af87ad
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0761
Les déclarations de méthode partielle de 'method\<T\>' ont des contraintes de paramètre de type incohérentes.  
  
 Si une méthode partielle a une implémentation, la contrainte de type générique doit être identique à la contrainte définie sur la signature de méthode.  
  
### Pour corriger cette erreur  
  
1.  Faites en sorte que les contraintes de type générique soient identiques sur chaque partie de la méthode partielle.  
  
## Exemple  
 Le code suivant génère l’erreur CS0761 :  
  
```  
// cs0761.cs using System; public partial class C { partial void Part<T>() where T : class; partial void Part<T>() where T : struct // CS0761 { } public static int Main() { return 1; } }  
  
```  
  
## Voir aussi  
 [Classes et méthodes partielles](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)   
 [Contraintes sur les paramètres de type](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)