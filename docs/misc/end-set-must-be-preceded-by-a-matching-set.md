---
title: "&#39;End Set&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Set&#39; correspondant | Microsoft Docs"
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
  - "bc30632"
  - "vbc30632"
helpviewer_keywords: 
  - "BC30632"
ms.assetid: 0c3dd065-566b-485c-9996-6177eb0fde39
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Set&#39; doit &#234;tre pr&#233;c&#233;d&#233; d’un &#39;Set&#39; correspondant
`End Set` est utilisé pour terminer les procédures de propriété `Set`. La construction `End Set` a été rencontrée à l’extérieur d’une procédure de propriété `Set`.  
  
 **ID d’erreur :** BC30632  
  
### Pour corriger cette erreur  
  
1.  Assurez\-vous que la procédure de propriété `Set` est déclarée après un mot clé `Property` et avant la construction `End Property`.  
  
2.  Assurez\-vous que la procédure de propriété `Set` commence par le mot clé `Set` et se termine par une construction `End Set`.  
  
## Voir aussi  
 [Property Statement](../Topic/Property%20Statement.md)   
 [Property Changes in Visual Basic](http://msdn.microsoft.com/fr-fr/1c138efa-9bc2-44d7-80a0-f3a7c2510264)