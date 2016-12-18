---
title: "Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3005 | Microsoft Docs"
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
  - "CS3005"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3005"
ms.assetid: 64b687e3-2dbd-45dd-b6da-81f77eb7d6bd
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3005
Un identificateur 'identifier' qui se différencie uniquement par la casse n’est pas conforme CLS  
  
 Un identificateur [public](../Topic/public%20\(C%23%20Reference\).md), [protected](../Topic/protected%20\(C%23%20Reference\).md) ou `protected` `internal`, qui diffère d’un autre identificateur `public`, `protected` ou `protected` `internal` uniquement par la casse d’une ou de plusieurs lettres n’est pas conforme avec CLS \(Common Language Specification\). Pour plus d’informations sur la conformité CLS, consultez [Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3) et [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS3003 :  
  
```  
// CS3005.cs using System; [assembly:CLSCompliant(true)] public class a { public static int a1 = 0; public static int A1 = 1;   // CS3005 public static void Main() { Console.WriteLine(a1); Console.WriteLine(A1); } }  
```