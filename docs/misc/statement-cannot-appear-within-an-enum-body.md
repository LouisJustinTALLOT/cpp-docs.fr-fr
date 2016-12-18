---
title: "Cette instruction ne peut pas appara&#238;tre dans le corps d’un Enum | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30619"
  - "bc30619"
helpviewer_keywords: 
  - "BC30619"
ms.assetid: 5d91d601-2a2d-418c-ae26-791d14a6f3cd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cette instruction ne peut pas appara&#238;tre dans le corps d’un Enum
Cette instruction ne peut pas apparaître dans le corps d’un Enum. Elle est interprétée comme la fin de l’Enum.  
  
 Une construction de langage inattendue a été rencontrée. Une construction `End Enum` est peut\-être manquante et tout code source après ce point est en dehors de l’énumération.  
  
 **ID d’erreur :** BC30619  
  
### Pour corriger cette erreur  
  
1.  Vérifiez la syntaxe du code utilisé à l’intérieur de l’énumération.  
  
2.  Vérifiez que la définition de l’interface se termine par une construction `End Enum`.  
  
## Voir aussi  
 [Enum Statement](../Topic/Enum%20Statement%20\(Visual%20Basic\).md)