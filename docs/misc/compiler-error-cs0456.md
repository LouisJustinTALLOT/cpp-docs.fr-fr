---
title: "Erreur du compilateur CS0456 | Microsoft Docs"
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
  - "CS0456"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0456"
ms.assetid: d714ec06-a7f4-405e-bf32-423696848319
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0456
Le paramètre de type 'nom\_paramètre\_type1' a la contrainte 'struct', donc 'nom\_paramètre\_type1' ne peut pas être utilisé comme contrainte pour 'nom\_paramètre\_type2'  
  
 Les contraintes de type valeur sont implicitement sealed. Ainsi, ces contraintes ne peuvent pas être utilisées comme contraintes sur un deuxième paramètre de type. Cela est dû au fait que les types valeur ne peuvent pas être substitués. Pour résoudre cette erreur, placez une contrainte de type valeur directement sur le deuxième paramètre de type, plutôt qu’indirectement par le premier paramètre de type.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0456.  
  
```  
// CS0456.cs // compile with: /target:library public class GenericsErrors { public class G5<T> where T : struct { public class N<U> where U : T {}   // CS0456 public class N2<U> where U : struct {}   // OK } }  
```