---
title: "Option /noconfig ignor&#233;e, car elle &#233;tait sp&#233;cifi&#233;e dans un fichier r&#233;ponse | Microsoft Docs"
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
  - "vbc2025"
  - "bc2025"
helpviewer_keywords: 
  - "BC2025"
ms.assetid: 87fb393d-e17f-4e50-8d98-d9dfeba30c3e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option /noconfig ignor&#233;e, car elle &#233;tait sp&#233;cifi&#233;e dans un fichier r&#233;ponse
L’option `/noconfig` indique au compilateur qu’il ne faut pas compiler avec le fichier Vbc.rsp. Toutefois, le compilateur traite le fichier Vbc.rsp avant tout autre fichier de réponse. Il ne donc peut pas honorer l’option `/noconfig` dans un fichier réponse.  
  
 **ID d’erreur :** BC2025  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’option `/noconfig` du fichier réponse.  
  
2.  Spécifiez l’option `/noconfig` quand vous appelez le compilateur de ligne de commande.  
  
## Voir aussi  
 [\/noconfig](../Topic/-noconfig.md)   
 [@ \(Specify Response File\)](../Topic/@%20\(Specify%20Response%20File\)%20\(Visual%20Basic\).md)