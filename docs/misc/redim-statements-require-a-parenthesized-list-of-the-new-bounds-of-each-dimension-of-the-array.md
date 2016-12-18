---
title: "Les instructions &#39;ReDim&#39; requi&#232;rent une liste entre parenth&#232;ses des nouvelles limites de chaque dimension du tableau | Microsoft Docs"
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
  - "bc30670"
  - "vbc30670"
helpviewer_keywords: 
  - "BC30670"
ms.assetid: b2c5fea3-e7db-4797-b917-d61a65befbd4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les instructions &#39;ReDim&#39; requi&#232;rent une liste entre parenth&#232;ses des nouvelles limites de chaque dimension du tableau
Vous devez spécifier la nouvelle taille d’un tableau dans le cadre d’une instruction `ReDim`.  
  
 **ID d’erreur :** BC30670  
  
### Pour corriger cette erreur  
  
-   Indiquez la taille de chaque rang du tableau. Par exemple :  
  
    ```  
    ReDim arr(5, 6)  
    ```  
  
## Voir aussi  
 [ReDim Statement](../Topic/ReDim%20Statement%20\(Visual%20Basic\).md)