---
title: "Les m&#233;thodes d&#233;clar&#233;es dans des structures ne peuvent pas comporter de clauses &#39;Handles&#39; | Microsoft Docs"
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
  - "vbc30728"
  - "bc30728"
helpviewer_keywords: 
  - "BC30728"
ms.assetid: 64c70bb5-3696-4865-8194-328394c2b4b1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les m&#233;thodes d&#233;clar&#233;es dans des structures ne peuvent pas comporter de clauses &#39;Handles&#39;
Les méthodes de structure ne peuvent pas utiliser le mot clé `Handles` pour gérer les événements.  
  
 **ID d’erreur :** BC30728  
  
### Pour corriger cette erreur  
  
-   Reconcevez votre structure en tant que classe.  
  
     Vous pouvez utiliser `AddHandler` pour associer un événement à un gestionnaire d’événements dans une structure, à condition que la structure implémente un gestionnaire d’événements défini dans une interface.  
  
## Voir aussi  
 [Structures and Classes](../Topic/Structures%20and%20Classes%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : Classes : modèles d’objets](http://msdn.microsoft.com/fr-fr/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : AddHandler et RemoveHandler](http://msdn.microsoft.com/fr-fr/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)