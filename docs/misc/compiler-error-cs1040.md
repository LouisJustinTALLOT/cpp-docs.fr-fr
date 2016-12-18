---
title: "Erreur du compilateur CS1040 | Microsoft Docs"
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
  - "CS1040"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1040"
ms.assetid: a988d665-ead5-489f-922d-ff2c4dd8a922
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1040
Les directives du préprocesseur doivent être le premier caractère \(autre qu'un espace blanc\) d'une ligne  
  
 Une [directive de préprocesseur](../Topic/C%23%20Preprocessor%20Directives.md) a été trouvée sur une ligne, mais elle n'était pas le premier jeton de cette ligne. Une directive doit être le premier jeton d’une ligne.  
  
 L’exemple suivant génère l’erreur CS1040 :  
  
```  
// CS1040.cs /* Define a symbol, X */ #define X   // CS1040 // try the following two lines instead // /* Define a symbol, X */ // #define X public class MyClass { public static void Main() { } }  
```