---
title: "Erreur du compilateur CS0315 | Microsoft Docs"
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
  - "CS0315"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0315"
ms.assetid: 9bb1cab3-1dca-4467-978b-1ab310901a70
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0315
Le type 'valueType' ne peut pas être utilisé comme paramètre de type 'T' dans le type générique ou la méthode 'TypeorMethod\<T\>'. Aucune conversion boxing de 'valueType'en 'referenceType' n’a lieu.  
  
 Cette erreur se produit quand vous limitez un type générique à une classe particulière et que vous tentez de construire une instance de cette classe à l’aide d’un type de valeur qui ne peut pas être converti implicitement en celui\-ci.  
  
### Pour corriger cette erreur  
  
1.  Une solution consiste à redéfinir la structure en tant que classe.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0315 :  
  
```  
// cs0315.cs public class ClassConstraint { } public struct ViolateClassConstraint { } public class Gen<T> where T : ClassConstraint { } public class Test { public static int Main() { Gen<ViolateClassConstraint> g = new Gen<ViolateClassConstraint>(); //CS0315 return 1; } }  
```  
  
## Voir aussi  
 [Contraintes sur les paramètres de type](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)   
 [Conversion boxing et unboxing](../Topic/Boxing%20and%20Unboxing%20\(C%23%20Programming%20Guide\).md)