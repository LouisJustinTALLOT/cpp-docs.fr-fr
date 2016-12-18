---
title: "&#39;&lt;nom_proc&#233;dure&gt;&#39; ne peut pas remplacer &#39;&lt;nom_proc&#233;dure_base&gt;&#39; car leurs contraintes de param&#232;tre de type diff&#232;rent | Microsoft Docs"
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
  - "BC32077"
  - "vbc32077"
helpviewer_keywords: 
  - "BC32077"
ms.assetid: 9be1a88d-c1a4-4f12-8e72-74abb2be565d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_proc&#233;dure&gt;&#39; ne peut pas remplacer &#39;&lt;nom_proc&#233;dure_base&gt;&#39; car leurs contraintes de param&#232;tre de type diff&#232;rent
Une procédure générique essaie de substituer une procédure de classe de base générique, mais leurs listes de contraintes sur leurs paramètres de type sont différentes.  
  
 Pour substituer une procédure de classe de base, la procédure de substitution doit correspondre non seulement à la signature complète de la procédure de classe de base, mais également au niveau d’accès de la procédure et au mécanisme de passage de chaque paramètre.  
  
 Pour substituer une procédure de classe de base générique, la procédure de substitution doit également correspondre au nombre de paramètres de type et à la liste de contraintes de chacun d’eux.  
  
 Pour plus d’informations sur les exigences de substitution, consultez [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md).  
  
 **ID d’erreur :** BC32077  
  
### Pour corriger cette erreur  
  
-   Si vous envisagez de substituer la procédure de classe de base, modifiez les contraintes de paramètre de type pour qu’elles correspondent exactement à celles de la procédure de classe de base.  
  
-   Si les contraintes de paramètre de type doivent rester inchangées, vous ne pouvez pas remplacer la procédure de classe de base. Supprimez le mot clé `Overrides` de la déclaration.  
  
## Voir aussi  
 [Types génériques Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)