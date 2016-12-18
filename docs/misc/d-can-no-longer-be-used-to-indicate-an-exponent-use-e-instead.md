---
title: "&#39;D&#39; ne peut plus &#234;tre utilis&#233; pour indiquer un exposant&#160;; utilisez &#39;E&#39; &#224; la place | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30827"
  - "bc30827"
helpviewer_keywords: 
  - "BC30827"
ms.assetid: 577f8c0b-9e8a-433f-b504-9ddaa936c250
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;D&#39; ne peut plus &#234;tre utilis&#233; pour indiquer un exposant&#160;; utilisez &#39;E&#39; &#224; la place
Vous ne pouvez pas utiliser le caractère 'D' pour indiquer l’élévation à la puissance.  
  
 **ID d’erreur :** BC30827  
  
### Pour corriger cette erreur  
  
-   Utilisez l’opérateur `^` ou les caractères `E+` pour indiquer la présence d’un exposant. Exemple :  
  
    ```  
    Const Mole = 6.02E+23 ' Same as 6.02D23 Const Mole2 = 6.02 * 10 ^ 23 ' Same as 6.02D23  
    ```  
  
## Voir aussi  
 [^ Operator](../Topic/%5E%20Operator%20\(Visual%20Basic\).md)   
 [Numeric Data Types](../Topic/Numeric%20Data%20Types%20\(Visual%20Basic\).md)