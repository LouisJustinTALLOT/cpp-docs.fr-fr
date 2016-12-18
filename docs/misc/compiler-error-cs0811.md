---
title: "Erreur du compilateur CS0811 | Microsoft Docs"
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
  - "CS0811"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0811"
ms.assetid: 99f81ad3-684f-47aa-adb8-360e24901454
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0811
Le nom complet de 'name' est trop long pour les informations de débogage. Compilez sans l’option '\/debug'.  
  
 Il existe des contraintes de taille sur les noms de variable et de type dans les informations de débogage.  
  
### Pour corriger cette erreur  
  
1.  Si la modification du nom n’est pas possible, la seule alternative consiste à compiler sans l’option [\/debug](../Topic/-debug%20\(C%23%20Compiler%20Options\).md).  
  
## Exemple  
 Le code suivant génère l’erreur CS0811 :  
  
```  
// cs0811.cs //Compile with: /debug using System; using System.Collections.Generic; namespace TestNamespace { using Long = List<List<List<List<List<List<List<List<List<List<List<List<List <List<List<List<List<List<List<List<List<List<List<List<List<List<List<List<int>>>>>>>>>>>>>>>>>>>>>>>>>>>>; // CS0811 class Test { static int Main() { return 1; } } }  
```