---
title: "Les enums doivent &#234;tre d&#233;clar&#233;s en tant que type int&#233;gral | Microsoft Docs"
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
  - "bc30650"
  - "vbc30650"
helpviewer_keywords: 
  - "BC30650"
ms.assetid: 566aa501-d283-4c1f-b494-3bc5fbe80e04
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les enums doivent &#234;tre d&#233;clar&#233;s en tant que type int&#233;gral
Les seuls types valides que vous pouvez utiliser dans les énumérations sont `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` et `ULong`. Aucun autre type de données ne peut être utilisé.  
  
 **ID d’erreur :** BC30650  
  
### Pour corriger cette erreur  
  
-   Spécifiez un type de données `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` ou `ULong`.  
  
## Voir aussi  
 [Data Types](../Topic/Data%20Type%20Summary%20\(Visual%20Basic\).md)   
 [Enum Statement](../Topic/Enum%20Statement%20\(Visual%20Basic\).md)