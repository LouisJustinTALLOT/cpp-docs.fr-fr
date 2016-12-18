---
title: "Une propri&#233;t&#233; &#39;WriteOnly&#39; doit fournir un &#39;Set&#39; | Microsoft Docs"
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
  - "bc30125"
  - "vbc30125"
helpviewer_keywords: 
  - "BC30125"
ms.assetid: c2b18086-9cd9-4094-b9a9-491c8d617096
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une propri&#233;t&#233; &#39;WriteOnly&#39; doit fournir un &#39;Set&#39;
Si une propriété est déclarée comme `WriteOnly`, elle doit fournir une procédure permettant d’écrire sa valeur.  
  
 **ID d’erreur :** BC30125  
  
### Pour corriger cette erreur  
  
1.  Veillez à inclure une procédure `Set` entre l’instruction `Property`et l’instruction `End Property`.  
  
2.  Vérifiez que les autres procédures de la déclaration `Property` se terminent correctement.  
  
## Voir aussi  
 [Property Statement](../Topic/Property%20Statement.md)   
 [Set Statement](../Topic/Set%20Statement%20\(Visual%20Basic\).md)