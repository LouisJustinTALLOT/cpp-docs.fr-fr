---
title: "Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3006 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3006"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3006"
ms.assetid: efbfd898-e46f-4c3d-91e2-e2da0056b016
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3006
La méthode surchargée 'method' qui se différencie uniquement au niveau de ref ou out, ou du rang de tableau, n’est pas conforme CLS  
  
 Une méthode ne peut pas être surchargée en fonction du paramètre [ref](../Topic/ref%20\(C%23%20Reference\).md) ou [out](../Topic/out%20\(C%23%20Reference\).md) et être toujours conforme à la spécification CLS \(Common Language Specification\). Pour plus d’informations sur la conformité CLS, consultez [Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3) et [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS3006. Pour résoudre cet avertissement, transformez en commentaire l’attribut de niveau assembly ou supprimez l’une des définitions de méthode.  
  
```  
// CS3006.cs using System; [assembly: CLSCompliant(true)] public class MyClass { public void f(int i) { } public void f(ref int i)   // CS3006 { } public static void Main() { } }  
```