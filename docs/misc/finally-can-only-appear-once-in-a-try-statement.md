---
title: "&#39;Finally&#39; ne peut appara&#238;tre qu’une seule fois dans une instruction &#39;Try&#39; | Microsoft Docs"
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
  - "vbc30381"
  - "bc30381"
helpviewer_keywords: 
  - "BC30381"
ms.assetid: 4fa1d5fa-c54a-4f8c-9d66-9dbcc38c53bf
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Finally&#39; ne peut appara&#238;tre qu’une seule fois dans une instruction &#39;Try&#39;
L’instruction `Finally` permet de terminer un bloc `Try...Catch...Finally` ; elle ne peut donc figurer qu’une seule fois à la fin du bloc.  
  
 **ID d’erreur :** BC30381  
  
### Pour corriger cette erreur  
  
1.  Supprimez le `Finally` redondant.  
  
## Voir aussi  
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [Vue d’ensemble de la gestion structurée des exceptions pour Visual Basic](http://msdn.microsoft.com/fr-fr/bb81af80-a735-4873-9711-6151a48e418a)