---
title: "Erreur du compilateur CS1023 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1023"
ms.assetid: 27d70f2c-9ae1-459c-a6be-01ed5a3eea07
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1023
L'instruction incorporée ne peut pas être une déclaration ni une instruction étiquetée  
  
 Une instruction incorporée, comme les instructions situées après une instruction **if**, ne peut pas contenir de déclarations ni d’instructions étiquetées.  
  
 L’exemple suivant génère l’erreur CS1023 à deux reprises :  
  
```  
// CS1023.cs public class a { public static void Main() { if (1) int i;      // CS1023, declaration is not valid here if (1) xx : i++;   // CS1023, labeled statement is not valid here } }  
```