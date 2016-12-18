---
title: "&#39;Option Compare&#39; doit &#234;tre suivi de &#39;Text&#39; ou &#39;Binary&#39; | Microsoft Docs"
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
  - "vbc30207"
  - "bc30207"
helpviewer_keywords: 
  - "BC30207"
ms.assetid: e59cf10d-47ce-401d-8474-3b69a3a5f5db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Option Compare&#39; doit &#234;tre suivi de &#39;Text&#39; ou &#39;Binary&#39;
Une instruction `Option Compare` contient un paramètre incorrect ou aucun paramètre. Les seuls paramètres autorisés dans `Option Compare` sont `Text` et `Binary`.  
  
 **ID d’erreur :** BC30207  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que le spécificateur de paramètre est bien orthographié.  
  
2.  Ajoutez `Text` ou `Binary` à l’instruction `Option Compare` ; par exemple, `Option Compare Text`.  
  
## Voir aussi  
 [Option Compare Statement](../Topic/Option%20Compare%20Statement.md)