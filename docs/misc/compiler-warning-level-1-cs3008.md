---
title: "Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3008 | Microsoft Docs"
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
  - "CS3008"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3008"
ms.assetid: 593f6114-bc7b-4789-958f-97bbf99c1c9f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3008
Un identificateur 'identifier' qui se différencie uniquement par la casse n’est pas conforme CLS  
  
 Un identificateur [public](../Topic/public%20\(C%23%20Reference\).md), [protected](../Topic/protected%20\(C%23%20Reference\).md) ou `protected` `internal` n’est pas conforme CLS s’il commence par un caractère de soulignement \(\_\). Pour plus d’informations sur la conformité CLS, consultez [Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3) et [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS3008 :  
  
```  
// CS3008.cs using System; [assembly:CLSCompliant(true)] public class a { public static int _a = 0;  // CS3008 // OK, private // private static int _a1 = 0; public static void Main() { } }  
```