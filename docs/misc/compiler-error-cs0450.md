---
title: "Erreur du compilateur CS0450 | Microsoft Docs"
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
  - "CS0450"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0450"
ms.assetid: 8eb0e98b-d7a1-49a7-8e55-36e2eb0057ff
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0450
'nom\_paramètre\_type' : impossible de spécifier une classe de contrainte et la contrainte 'class' ou 'struct'  
  
 Si un paramètre de type est contraint par la contrainte de type struct, il est logiquement contradictoire qu’il soit également contraint par un type class spécifique, puisque struct et class sont des catégories mutuellement exclusives. Si un paramètre de type est contraint par une contrainte de type class spécifique, il est par définition contraint par la contrainte de type class. Spécifier la contrainte de type class est donc redondant.  
  
## Exemple  
  
```  
// CS0450.cs // compile with: /t:library public class GenericsErrors { public class B { } public class G3<T> where T : struct, B { } // CS0450 // To resolve, use the following line instead: // public class G3<T> where T : B { } }  
```