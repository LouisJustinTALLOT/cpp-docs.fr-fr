---
title: "Impossible de cr&#233;er une instance de Module &#39;&lt;nom_module&gt;&#39; | Microsoft Docs"
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
  - "bc30166"
  - "vbc30166"
helpviewer_keywords: 
  - "BC30166"
ms.assetid: 40b9dbd3-9b57-450f-a631-b0ab06ca19c4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de cr&#233;er une instance de Module &#39;&lt;nom_module&gt;&#39;
Un module existe uniquement en tant qu’instance partagée unique. Vous ne pouvez pas créer d’instances supplémentaires.  
  
 **ID d’erreur :** BC30166  
  
### Pour corriger cette erreur  
  
-   Remplacez le module par une classe, ou remplacez\-le dans la clause `New` par un nom de classe.  
  
## Voir aussi  
 [Module Statement](../Topic/Module%20Statement.md)   
 [NOT IN BUILD : Implements, mot clé et instruction](http://msdn.microsoft.com/fr-fr/b96560f7-6413-480f-a1e2-f80253bab5be)