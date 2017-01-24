---
title: "&#39;GoTo &lt;nom_&#233;tiquette&gt;&#39; n’est pas valide, car &#39;&lt;nom_&#233;tiquette&gt;&#39; se trouve &#224; l’int&#233;rieur d’une instruction &#39;For&#39; ou &#39;For Each&#39; qui ne contient pas cette instruction | Microsoft Docs"
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
  - "vbc30757"
  - "bc30757"
helpviewer_keywords: 
  - "BC30757"
ms.assetid: be28bec5-1bc4-4da1-ba0c-4e3faac81077
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;nom_&#233;tiquette&gt;&#39; n’est pas valide, car &#39;&lt;nom_&#233;tiquette&gt;&#39; se trouve &#224; l’int&#233;rieur d’une instruction &#39;For&#39; ou &#39;For Each&#39; qui ne contient pas cette instruction
Les instructions `GoTo` sont limitées à des sauts dans le bloc de code actuel.  
  
 **ID d’erreur :** BC30757  
  
### Pour corriger cette erreur  
  
-   Restructurez votre code pour que l’instruction `GoTo` et l’étiquette se trouvent à l’intérieur du bloc `For`.  
  
## Voir aussi  
 [GoTo Statement](../Topic/GoTo%20Statement.md)   
 [For \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/c470a263-9b49-4308-8fd6-8592b84a7980)