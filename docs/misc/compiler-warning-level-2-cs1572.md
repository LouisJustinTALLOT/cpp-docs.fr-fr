---
title: "Avertissement du compilateur (niveau&#160;2) CS1572 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1572"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1572"
ms.assetid: 24bc8b96-29d2-4201-bc4e-6b9b5a4f5a1d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS1572
Le commentaire XML sur 'construction' a une balise param pour 'paramètre', alors qu’il n’existe aucun paramètre de ce nom  
  
 Lors de l’utilisation de l’option du compilateur [\/doc](../Topic/-doc%20\(C%23%20Compiler%20Options\).md), vous avez spécifié un commentaire pour un paramètre qui n’existe pas pour la méthode. Modifiez la valeur passée à l’attribut name ou supprimez l’une des lignes de commentaire.  
  
 L’exemple suivant génère l’avertissement CS1572 :  
  
```  
// CS1572.cs // compile with: /W:2 /doc:x.xml /// <summary>help text</summary> public class MyClass { /// <param name='Int1'>Used to indicate status.</param> /// <param name='Char1'>Used to indicate status.</param> /// <param name='Char2'>???</param> // CS1572 public static void MyMethod(int Int1, char Char1) { } /// <summary>help text</summary> public static void Main () { } }  
```