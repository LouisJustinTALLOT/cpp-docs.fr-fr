---
title: "&#39;GoTo &lt;&#233;tiquette_ligne&gt;&#39; n’est pas valide, car &#39;&lt;&#233;tiquette_ligne&gt;&#39; se trouve dans une instruction &#39;Using&#39; qui ne contient pas cette instruction | Microsoft Docs"
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
  - "bc36009"
  - "vbc36009"
helpviewer_keywords: 
  - "BC36009"
ms.assetid: ebec3cac-d378-4e9b-a792-12e9ece5599e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;&#233;tiquette_ligne&gt;&#39; n’est pas valide, car &#39;&lt;&#233;tiquette_ligne&gt;&#39; se trouve dans une instruction &#39;Using&#39; qui ne contient pas cette instruction
Une instruction `GoTo` à l’extérieur d’une construction `Using` essaie d’effectuer un branchement vers une étiquette de ligne à l’intérieur de la construction.  
  
 Il n’est pas possible d’effectuer un branchement depuis n’importe quel emplacement à l’extérieur d’une construction `Using`...`End Using` vers n’importe quel emplacement à l’intérieur de cette dernière.  
  
 **ID d’erreur :** BC36009  
  
### Pour corriger cette erreur  
  
-   Remplacez l’étiquette de ligne de l’instruction `GoTo` par une étiquette qui n’est pas à l’intérieur d’une construction `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With` ou `Using`...`End Using`.  
  
     ou  
  
-   Supprimez totalement l’instruction `GoTo`. La seule façon d’entrer dans une construction `Using`...`End Using` est de permettre que le contrôle passe à l’instruction `Using` elle\-même.  
  
## Voir aussi  
 [GoTo Statement](../Topic/GoTo%20Statement.md)   
 [Using Statement](../Topic/Using%20Statement%20\(Visual%20Basic\).md)