---
title: "Erreur du compilateur CS1560 | Microsoft Docs"
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
  - "CS1560"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1560"
ms.assetid: 772c4543-6c8d-453f-ae3f-d333528eb8b3
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1560
Nom de fichier spécifié non valide pour la directive de préprocesseur Nom de fichier trop long ou non valide  
  
 Le nom de fichier spécifié avec [\#line](../Topic/%23line%20\(C%23%20Reference\).md) dépasse \_MAX\_PATH \(256 caractères\) ou la ligne sur laquelle `#line` a été détecté dépasse 2 000 caractères.  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS1560.  
  
```  
// cs1560.cs using System; class MyClass { public static void Main() { Console.WriteLine("Normal line #1."); #line 21 "MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890.txt"   // CS1560 } }  
```