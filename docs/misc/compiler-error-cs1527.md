---
title: "Erreur du compilateur CS1527 | Microsoft Docs"
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
  - "CS1527"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1527"
ms.assetid: a0d52130-d6da-41bb-b153-8e96cbb7e316
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1527
Les éléments définis dans un espace de noms ne peuvent pas être explicitement déclarés comme private, protected ou protected internal  
  
 Les déclarations de type d’un espace de noms peuvent avoir un accès [public](../Topic/public%20\(C%23%20Reference\).md) ou [internal](../Topic/internal%20\(C%23%20Reference\).md). Si aucune accessibilité n’est spécifiée, la valeur par défaut est **internal**.  
  
 L’exemple suivant génère l’erreur CS1527 :  
  
```  
// CS1527.cs namespace Sample { private class C1 {};             // CS1527 protected class C2 {};           // CS1527 protected internal class C3 {};  // CS1527 }  
```  
  
 L’exemple suivant génère l’erreur CS1527, car quand aucun espace de noms n’est déclaré explicitement dans le code de votre programme, toutes les déclarations de type sont situées implicitement dans l’espace de noms global.  
  
```  
//cs1527_2.cs using System; protected class C4{} private struct S1{}  
```  
  
## Voir aussi  
 [Espaces de noms](../Topic/Namespaces%20\(C%23%20Programming%20Guide\).md)   
 [global](../Topic/global%20\(C%23%20Reference\).md)   
 [::, opérateur](../Topic/::%20Operator%20\(C%23%20Reference\).md)   
 [Domaine d'accessibilité](../Topic/Accessibility%20Domain%20\(C%23%20Reference\).md)   
 [Modificateurs d'accès](../Topic/Access%20Modifiers%20\(C%23%20Programming%20Guide\).md)