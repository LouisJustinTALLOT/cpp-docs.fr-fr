---
title: "Erreur du compilateur CS1010 | Microsoft Docs"
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
  - "CS1010"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1010"
ms.assetid: 3d47277a-253f-464b-a603-e3b37e0e7b0d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1010
Saut de ligne dans la constante  
  
 Une [chaîne](../Topic/string%20\(C%23%20Reference\).md) n’a pas été correctement délimitée.  
  
 L’exemple suivant génère l’erreur CS1010 :  
  
```  
// CS1010.cs class Sample { static void Main() { string a = "Hello World;   // CS1010 // Use the following line, with end quote before semicolon: string a = "Hello World"; // } }  
```  
  
## Voir aussi  
 [NIB \- Chaînes \(Guide de programmation C\#\)](http://msdn.microsoft.com/fr-fr/1a32b1c9-0d99-468a-9734-e3a47f2e897a)