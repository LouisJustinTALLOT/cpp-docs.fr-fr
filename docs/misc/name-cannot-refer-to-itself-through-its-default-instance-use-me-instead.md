---
title: "&#39;&lt;nom&gt;&#39; ne peut pas se r&#233;f&#233;rer &#224; lui-m&#234;me via son instance par d&#233;faut&#160;; utilisez &#39;Me&#39; &#224; la place | Microsoft Docs"
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
  - "vbc31139"
  - "bc31139"
helpviewer_keywords: 
  - "BC31139"
ms.assetid: 459e5d5a-d526-4cd0-934e-96e4e1eb51bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom&gt;&#39; ne peut pas se r&#233;f&#233;rer &#224; lui-m&#234;me via son instance par d&#233;faut&#160;; utilisez &#39;Me&#39; &#224; la place
Vous avez essayé de faire référence à un formulaire en tant qu’instance par défaut à partir de l’intérieur de ce formulaire. Le formulaire risque de s’appeler lui\-même de manière récursive.  
  
 Dans la plupart des cas, vous devez utiliser `Me` quand vous faites référence à l’instance actuelle du formulaire, au lieu d’utiliser l’instance par défaut.  
  
 **ID d’erreur :** BC31139  
  
### Pour corriger cette erreur  
  
-   Utilisez `Me` pour faire référence à l’objet.  
  
## Voir aussi  
 [Principes de base du débogueur](../Topic/Debugger%20Basics.md)