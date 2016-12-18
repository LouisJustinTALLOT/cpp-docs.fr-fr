---
title: "Les instructions &#39;Declare&#39; dans un Module ne peuvent pas &#234;tre d&#233;clar&#233;es &#39;&lt;sp&#233;cificateur&gt;&#39; | Microsoft Docs"
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
  - "vbc30786"
  - "bc30786"
helpviewer_keywords: 
  - "BC30786"
ms.assetid: 488b855f-72ea-414b-bffc-a5b63e97d289
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les instructions &#39;Declare&#39; dans un Module ne peuvent pas &#234;tre d&#233;clar&#233;es &#39;&lt;sp&#233;cificateur&gt;&#39;
Une déclaration `Declare` possède un spécificateur qui n’est pas valide dans une déclaration `Module`. Les modules ne peuvent jamais être instanciés, ils ne prennent pas en charge l’héritage et ils ne peuvent pas implémenter d’interfaces.  
  
 **ID d’erreur :** BC30786  
  
### Pour corriger cette erreur  
  
-   Supprimez le spécificateur.  
  
## Voir aussi  
 [Delegate Statement](../Topic/Delegate%20Statement.md)   
 [Module Statement](../Topic/Module%20Statement.md)