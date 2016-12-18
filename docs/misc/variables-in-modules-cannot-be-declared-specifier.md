---
title: "Les variables des modules ne peuvent pas &#234;tre d&#233;clar&#233;es &#39;&lt;sp&#233;cificateur&gt;&#39; | Microsoft Docs"
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
  - "bc30593"
  - "vbc30593"
helpviewer_keywords: 
  - "BC30593"
ms.assetid: 2500b776-7fa4-4272-8cc7-204593706651
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les variables des modules ne peuvent pas &#234;tre d&#233;clar&#233;es &#39;&lt;sp&#233;cificateur&gt;&#39;
Vous avez utilisé un spécificateur, tel que `MustInherit`, sur une variable dans une instruction `Module`. Les modules ne peuvent jamais être instanciés, ils ne prennent pas en charge l’héritage et ils ne peuvent pas implémenter d’interfaces.  
  
 **ID d’erreur :** BC30593  
  
### Pour corriger cette erreur  
  
-   Supprimez le spécificateur.  
  
## Voir aussi  
 [Module Statement](../Topic/Module%20Statement.md)