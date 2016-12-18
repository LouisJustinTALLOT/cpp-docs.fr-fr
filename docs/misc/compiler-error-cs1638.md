---
title: "Erreur du compilateur CS1638 | Microsoft Docs"
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
  - "CS1638"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1638"
ms.assetid: 5279c060-5be3-4c29-80cc-21326d4cffdb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1638
'identificateur' est un identificateur réservé et ne peut pas être utilisé lorsque le mode langage version ISO est utilisé  
  
 Quand l’option de compatibilité de langage ISO est spécifiée par le commutateur du compilateur **\/langversion**, un identificateur comportant deux traits de soulignement, où qu’ils soient dans l’identificateur, génère cette erreur. Pour éviter cette erreur, supprimez les identificateurs présentant deux traits de soulignement ou n’utilisez pas l’option de langage version ISO\-1.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1638 :  
  
```  
// CS1638.cs // compile with: /langversion:ISO-1 class bad__identifer // CS1638 (double underscores are not ISO compliant) { } // Try this instead: //class GoodIdentifier //{ //} class CMain { public static void Main() { } }  
```  
  
## Voir aussi  
 [\/langversion \(Conformant Syntax\)](../Topic/-langversion%20\(C%23%20Compiler%20Options\).md)