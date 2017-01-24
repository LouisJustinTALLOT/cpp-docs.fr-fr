---
title: "Les instructions &#39;GoSub&#39; ne sont plus prises en charge | Microsoft Docs"
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
  - "vbc30814"
  - "bc30814"
helpviewer_keywords: 
  - "BC30814"
ms.assetid: fef2d78f-39ba-4aad-93b3-c7a08df9f805
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les instructions &#39;GoSub&#39; ne sont plus prises en charge
`GoSub` ne peut pas être utilisé pour appeler une procédure.  
  
 **ID d’erreur :** BC30814  
  
### Pour corriger cette erreur  
  
-   Appelez directement les procédures sans utiliser `GoSub`. Par exemple :  
  
    ```  
    CalculateInterest(Amount, Rate, Time)  
    ```  
  
## Voir aussi  
 [Procedures](../Topic/Procedures%20in%20Visual%20Basic.md)