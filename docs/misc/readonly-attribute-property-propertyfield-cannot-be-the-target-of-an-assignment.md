---
title: "La propri&#233;t&#233; d’attribut &#39;ReadOnly&#39; &#39;&lt;champ_propri&#233;t&#233;&gt;&#39; ne peut pas &#234;tre la cible d’une assignation | Microsoft Docs"
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
  - "bc31501"
  - "vbc31501"
helpviewer_keywords: 
  - "BC31501"
ms.assetid: 41c3f979-6b24-4595-9503-9c80a4d6d762
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propri&#233;t&#233; d’attribut &#39;ReadOnly&#39; &#39;&lt;champ_propri&#233;t&#233;&gt;&#39; ne peut pas &#234;tre la cible d’une assignation
Une tentative a été effectuée pour affecter une valeur à une propriété `ReadOnly` dans un attribut.  
  
 **ID d’erreur :** BC31501  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’instruction d’assignation de propriété.  
  
2.  Si vous utilisez des propriétés que vous avez développées, supprimez les modificateurs `ReadOnly` ou `Shared` de la propriété d’attribut.  
  
## Voir aussi  
 [Shared](../Topic/Shared%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : Attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)