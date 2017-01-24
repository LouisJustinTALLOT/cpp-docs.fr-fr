---
title: "&#39;GoTo &lt;labelname&gt;&#39; n’est pas valide car &#39;GoTo &lt;nom_&#233;tiquette&gt;&#39; est &#224; l’int&#233;rieur d’une instruction &#39;With&#39; qui ne contient pas cette instruction | Microsoft Docs"
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
  - "bc30756"
  - "vbc30756"
helpviewer_keywords: 
  - "BC30756"
ms.assetid: 9c39d4ad-0b9b-45e9-b6c2-d983144b5b23
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;labelname&gt;&#39; n’est pas valide car &#39;GoTo &lt;nom_&#233;tiquette&gt;&#39; est &#224; l’int&#233;rieur d’une instruction &#39;With&#39; qui ne contient pas cette instruction
Les instructions `GoTo` sont limitées à des sauts dans le bloc de code actuel.  
  
 **ID d’erreur :** BC30756  
  
### Pour corriger cette erreur  
  
-   Restructurez votre code pour que l’instruction `GoTo` et l’étiquette se trouvent à l’intérieur du bloc `With`.  
  
## Voir aussi  
 [GoTo Statement](../Topic/GoTo%20Statement.md)