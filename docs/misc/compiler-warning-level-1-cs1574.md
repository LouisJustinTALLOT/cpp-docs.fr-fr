---
title: "Avertissement du compilateur (niveau&#160;1) CS1574 | Microsoft Docs"
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
  - "CS1574"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1574"
ms.assetid: 4cd2b474-ab01-4397-aed7-63e5f0081649
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS1574
Le commentaire XML sur 'construction' comporte une erreur de syntaxe au niveau de l’attribut cref 'nom'  
  
 Une chaîne passée à une balise cref, par exemple, dans une balise \<exception\>, a référencé un membre qui n’est pas disponible dans l’environnement de génération actuel. La chaîne que vous passez à une balise cref doit correspondre au nom d’un membre ou d’un champ ayant une syntaxe correcte.  
  
 Pour plus d’informations, consultez [Balises recommandées pour commentaires de documentation](../Topic/Recommended%20Tags%20for%20Documentation%20Comments%20\(C%23%20Programming%20Guide\).md).  
  
 L’exemple suivant génère l’erreur CS1574 :  
  
```  
// CS1574.cs // compile with: /W:1 /doc:x.xml using System; /// <exception cref="System.Console.WriteLin">An exception class.</exception>   // CS1574 // instead, uncomment and try the following line // /// <exception cref="System.Console.WriteLine">An exception class.</exception> class EClass : Exception { } class TestClass { public static void Main() { try { } catch(EClass) { } } }  
```