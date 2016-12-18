---
title: "Variable locale inutilis&#233;e&#160;: &#39;&lt;nom_variable_locale&gt;&#39; | Microsoft Docs"
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
  - "vbc42024"
  - "BC42024"
helpviewer_keywords: 
  - "BC42024"
ms.assetid: 749b1315-0f85-4f7e-b68b-8cc4346c502b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Variable locale inutilis&#233;e&#160;: &#39;&lt;nom_variable_locale&gt;&#39;
Une variable locale dans une procédure est déclarée, mais jamais utilisée.  
  
 Il se peut qu’il y ait une faute d’orthographe dans les variables locales de la procédure. Si cette variable est utilisée dans une autre instruction mais orthographiée différemment, il s’agit pour le compilateur de deux variables différentes.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **ID d’erreur :** BC42024  
  
### Pour corriger cette erreur  
  
1.  Vérifiez si les variables locales de la procédure comportent des fautes d’orthographe. Notez que la casse ne fait pas de différence. Les noms `ABC` et `abc` sont considérés comme faisant référence à la même variable.  
  
2.  S’il n’y a pas de faute d’orthographe, supprimez la déclaration de cette variable ou utilisez\-la dans une autre instruction dans la procédure.  
  
## Voir aussi  
 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)   
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)