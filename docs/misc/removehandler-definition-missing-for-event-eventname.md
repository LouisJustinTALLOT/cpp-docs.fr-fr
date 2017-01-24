---
title: "La d&#233;finition &#39;RemoveHandler&#39; est manquante pour l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; | Microsoft Docs"
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
  - "bc31131"
  - "vbc31131"
helpviewer_keywords: 
  - "BC31131"
ms.assetid: 0ef68daf-b66e-4ecf-bf2c-dcacabd8aa3d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La d&#233;finition &#39;RemoveHandler&#39; est manquante pour l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39;
Si un événement est déclaré comme `Custom`, il doit fournir une procédure pour supprimer un gestionnaire d’événements.  
  
 **ID d’erreur :** BC31131  
  
### Pour corriger cette erreur  
  
1.  Placez une déclaration `RemoveHandler` entre l’instruction `Custom Event` et l’instruction `End Event`.  
  
2.  Vérifiez que les autres procédures de la déclaration d’événement se terminent correctement.  
  
## Voir aussi  
 [RemoveHandler Statement](../Topic/RemoveHandler%20Statement.md)   
 [Event Statement](../Topic/Event%20Statement.md)