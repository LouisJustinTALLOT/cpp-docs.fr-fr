---
title: "Erreur du compilateur CS1959 | Microsoft Docs"
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
  - "CS1959"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1959"
ms.assetid: 20a31619-3e30-446a-becc-a7f8cfcec66d
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1959
'name' est de type 'type'. Le type spécifié dans une déclaration de constante doit être sbyte, byte, short, ushort, int, uint, long, ulong, char, float, double, decimal, bool, string, un type enum ou un type référence.  
  
 Les types autorisés dans une déclaration Const sont limités à ceux décrits dans ce message.  
  
### Pour corriger cette erreur  
  
1.  Déclarez la constante avec un type autorisé.  
  
## Exemple  
 Le code suivant génère l’erreur CS1959, car `null` n’est pas un type.  
  
```  
// cs1959.cs class Program { static void Test<T>() where T : class { const T x = null; // CS1959 } }  
```  
  
## Voir aussi  
 [Constantes](../Topic/Constants%20\(C%23%20Programming%20Guide\).md)   
 [null](../Topic/null%20\(C%23%20Reference\).md)