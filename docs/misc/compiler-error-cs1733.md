---
title: "Erreur du compilateur CS1733 | Microsoft Docs"
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
  - "CS1733"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1733"
ms.assetid: 2188aabe-404d-4a95-a11a-736dbd848508
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1733
Expression attendue.  
  
 Cette erreur se produit chaque fois que le compilateur attend une expression sur la ligne où l’erreur s’est produite. Dans l’exemple suivant, la virgule de fin dans l’initialiseur indique au compilateur qu’une autre expression va suivre.  
  
### Pour corriger cette erreur  
  
-   Fournissez l’expression manquante.  
  
-   Supprimez les jetons qui entraînent l’attente d’une expression par le compilateur.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS1733 en raison de la virgule de fin :  
  
```  
// cs1733.cs using System.Collections.Generic; public class Test { public static void Main() { List<int> list = new List<int>() {{ 1, 2, }};// CS1733 } }  
```