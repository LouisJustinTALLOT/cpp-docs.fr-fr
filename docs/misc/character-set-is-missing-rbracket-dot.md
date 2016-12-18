---
title: "Character set is missing &#39;]&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_RE_SETMISSINGCLOSE"
  - "vs.message.0x800A00C0"
ms.assetid: 97d2436c-498d-4eb0-a08c-8efcc7797fc0
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Character set is missing &#39;]&#39;.
Cette erreur se produit généralement lorsque le crochet fermant \(`]`\) est absent dans une expression régulière spécifiée pour une chaîne de recherche ou de remplacement.  
  
### Pour corriger cette erreur  
  
1.  Pour rechercher le caractère `]`, utilisez `\]`.  
  
2.  Pour utiliser un jeu de caractères, entrez le crochet fermant `]`.  
  
## Voir aussi  
 [Utilisation d'expressions régulières dans Visual Studio](../Topic/Using%20Regular%20Expressions%20in%20Visual%20Studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/fr-fr/dad03582-4931-4893-83ba-84b37f5b1600)   
 [Rechercher dans les fichiers](../Topic/Find%20in%20Files.md)