---
title: "Une variable de contr&#244;le de boucle ne peut pas &#234;tre une propri&#233;t&#233; ni un tableau index&#233; &#224; liaison tardive | Microsoft Docs"
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
  - "bc30039"
  - "vbc30039"
helpviewer_keywords: 
  - "BC30039"
ms.assetid: 63846449-b1df-4626-bf99-36fa9b187799
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une variable de contr&#244;le de boucle ne peut pas &#234;tre une propri&#233;t&#233; ni un tableau index&#233; &#224; liaison tardive
La variable utilisée pour itérer au sein d’une boucle `For` doit être un type de données numérique.  
  
 **ID d’erreur :** BC30039  
  
### Pour corriger cette erreur  
  
-   Modifiez la déclaration de la variable de contrôle de boucle pour spécifier `Integer`, `Short`, `Long`, `Byte`, `Single`, `Double` ou `Decimal`.  
  
## Voir aussi  
 [For...Next, instruction](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)