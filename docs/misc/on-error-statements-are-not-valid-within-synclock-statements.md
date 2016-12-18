---
title: "Les instructions &#39;On Error&#39; ne sont pas valides dans les instructions &#39;SyncLock&#39; | Microsoft Docs"
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
  - "bc30752"
  - "vbc30752"
helpviewer_keywords: 
  - "BC30752"
ms.assetid: 5c726627-b0fc-4edf-bd29-a83a0009f44d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les instructions &#39;On Error&#39; ne sont pas valides dans les instructions &#39;SyncLock&#39;
Vous ne pouvez pas utiliser les instructions `On Error` dans des blocs `SyncLock`, car elles interrompraient la synchronisation du thread.  
  
 **ID d’erreur :** BC30752  
  
### Pour corriger cette erreur  
  
1.  Placez les instructions `On Error` à l’extérieur des blocs `SyncLock`.  
  
## Voir aussi  
 [On Error Statement](../Topic/On%20Error%20Statement%20\(Visual%20Basic\).md)