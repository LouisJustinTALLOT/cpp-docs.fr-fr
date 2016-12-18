---
title: "Erreur du compilateur CS0227 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0227"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0227"
ms.assetid: b595a1c9-8204-4ff7-a1d0-258b0b1d6ff7
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0227
Du code unsafe ne peut apparaître qu'en cas de compilation avec \/unsafe  
  
 Si le code source contient le mot clé [unsafe](../Topic/unsafe%20\(C%23%20Reference\).md), vous devez aussi utiliser l’option du compilateur [\/unsafe](../Topic/-unsafe%20\(C%23%20Compiler%20Options\).md). Pour plus d'informations, consultez [Pointeurs et code unsafe](../Topic/Unsafe%20Code%20and%20Pointers%20\(C%23%20Programming%20Guide\).md).  
  
 Pour définir l’option unsafe dans [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], cliquez sur **Projet** dans le menu principal, sélectionnez le volet **Build**, puis cochez la case « Autoriser le code unsafe ».  
  
 L’exemple suivant, quand il est compilé sans **\/unsafe**, génère l’erreur CS0227 :  
  
```  
// CS0227.cs public class MyClass { unsafe public static void Main()   // CS0227 { } }  
```  
  
## Voir aussi  
 [C\# Compiler Errors](../Topic/C%23%20Compiler%20Errors.md)