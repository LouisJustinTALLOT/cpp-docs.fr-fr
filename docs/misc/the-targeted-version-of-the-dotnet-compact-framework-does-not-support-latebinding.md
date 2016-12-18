---
title: "La version cibl&#233;e du .NET Compact Framework ne prend pas en charge la liaison tardive | Microsoft Docs"
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
  - "vbc30762"
  - "bc30762"
helpviewer_keywords: 
  - "BC30762"
ms.assetid: b433014d-8422-46e8-ad55-321146a48186
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La version cibl&#233;e du .NET Compact Framework ne prend pas en charge la liaison tardive
La version du .NET Compact Framework que vous utilisez ne prend pas en charge la liaison tardive.  
  
 **ID d’erreur :** BC30762  
  
### Pour corriger cette erreur  
  
1.  Évitez d’appeler des fonctions, des sous\-routines ou des propriétés sur une variable déclarée comme objet.  
  
2.  Évitez d’utiliser la variable objet comme tableau.  
  
3.  Évitez d’utiliser des expressions d’accès au membre de dictionnaire avec des variables objet.  
  
## Voir aussi  
 [NotInBuild : Objets en Visual Basic](http://msdn.microsoft.com/fr-fr/85bd757a-a19e-45e1-af89-d68765f5ee3c)   
 [Special Characters in Code](../Topic/Special%20Characters%20in%20Code%20\(Visual%20Basic\).md)