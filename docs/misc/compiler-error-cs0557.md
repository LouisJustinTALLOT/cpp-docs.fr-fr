---
title: "Erreur du compilateur CS0557 | Microsoft Docs"
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
  - "CS0557"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0557"
ms.assetid: beca353e-4fea-4e4f-a48a-eddeebb153bb
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0557
La conversion définie par l’utilisateur dans le type 'class' est en double  
  
 Les routines de conversion en double ne sont pas autorisées dans une classe.  
  
 L’exemple suivant génère l’erreur CS0557 :  
  
```  
// CS0557.cs namespace x { public class ii { public class iii { public static implicit operator int(iii aa) { return 0; } // CS0557, delete duplicate public static explicit operator int(iii aa) { return 0; } } public static void Main() { } } }  
```