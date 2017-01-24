---
title: "Erreur du compilateur&#160;CS1103 | Microsoft Docs"
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
  - "CS1103"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1103"
ms.assetid: 513a26ea-9d66-4dc3-b3e6-d709c3089b1a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur&#160;CS1103
Le premier paramètre d’une méthode d’extension ne peut pas être de type 'type'  
  
 Le premier paramètre d’une méthode d’extension ne peut pas être un type pointeur.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1103 :  
  
```  
// cs1103.cs public static class Extensions { public unsafe static char* Test(this char* charP) { return charP; } // CS1103 }   
```  
  
## Voir aussi  
 [Méthodes d'extension](../Topic/Extension%20Methods%20\(C%23%20Programming%20Guide\).md)   
 [unsafe](../Topic/unsafe%20\(C%23%20Reference\).md)