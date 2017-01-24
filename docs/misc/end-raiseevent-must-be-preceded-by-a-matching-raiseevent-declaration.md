---
title: "&#39;End RaiseEvent&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’une d&#233;claration &#39;RaiseEvent&#39; correspondante | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31126"
  - "bc31126"
helpviewer_keywords: 
  - "BC31126"
ms.assetid: 8f445128-eb5f-4610-9cec-107180871500
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End RaiseEvent&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’une d&#233;claration &#39;RaiseEvent&#39; correspondante
Une instruction `End RaiseEvent` s’est produite sans instruction `RaiseEvent` correspondante.`End RaiseEvent` doit être précédé d’une instruction `RaiseEvent` correspondante.  
  
 **ID d’erreur :** BC31126  
  
### Pour corriger cette erreur  
  
-   Vérifiez que l’instruction `RaiseEvent` précédente est valide et orthographiée correctement.  
  
## Voir aussi  
 [RaiseEvent Statement](../Topic/RaiseEvent%20Statement.md)   
 [Event Statement](../Topic/Event%20Statement.md)