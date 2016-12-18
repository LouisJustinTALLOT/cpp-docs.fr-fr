---
title: "&#39;&lt;m&#233;thode1&gt;&#39; et &#39;&lt;m&#233;thode2&gt;&#39; ne peuvent pas se surcharger mutuellement, car seuls les param&#232;tres optionnels les diff&#233;rencient | Microsoft Docs"
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
  - "vbc30300"
  - "bc30300"
helpviewer_keywords: 
  - "BC30300"
ms.assetid: adb44ceb-57a0-4123-8fd8-7eb83c3f601f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;thode1&gt;&#39; et &#39;&lt;m&#233;thode2&gt;&#39; ne peuvent pas se surcharger mutuellement, car seuls les param&#232;tres optionnels les diff&#233;rencient
Vous avez tenté de surcharger une méthode avec une autre méthode qui se distingue de la première uniquement par ses paramètres facultatifs. Une méthode assortie d’un paramètre facultatif équivaut à deux méthodes surchargées, une avec le paramètre facultatif et l’autre sans. Par conséquent, vous ne pouvez pas surcharger une méthode avec une liste d’arguments correspondant aux deux.  
  
 **ID d’erreur :** BC30300  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les méthodes se distinguent autrement que par les paramètres facultatifs.  
  
## Voir aussi  
 [Procedure Overloading](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)   
 [Considerations in Overloading Procedures](../Topic/Considerations%20in%20Overloading%20Procedures%20\(Visual%20Basic\).md)