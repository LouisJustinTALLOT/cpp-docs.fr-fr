---
title: "Les informations pour le type de &#39;&lt;nom_type&gt;&#39; n’ont pas &#233;t&#233; charg&#233;es dans le runtime | Microsoft Docs"
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
  - "vbc30750"
  - "bc30750"
helpviewer_keywords: 
  - "BC30750"
ms.assetid: b0f074f9-571d-48f8-b334-4fd34b61cd89
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les informations pour le type de &#39;&lt;nom_type&gt;&#39; n’ont pas &#233;t&#233; charg&#233;es dans le runtime
Un type qui n’a pas été chargé par le runtime a été référencé.  
  
 **ID d’erreur :** BC30750  
  
### Pour corriger cette erreur  
  
1.  Restructurez votre code pour que le type soit défini dans la portée actuelle.  
  
2.  Vérifiez que le membre est défini et que vous avez correctement orthographié son nom.  
  
3.  Essayez d’accéder à l’un des membres déclarés dans le module. Dans certains cas, l’environnement de débogage ne peut pas localiser les membres, car les modules dans lesquels ils sont déclarés ne sont pas chargés.  
  
## Voir aussi  
 [Débogage dans Visual Studio](../Topic/Debugging%20in%20Visual%20Studio.md)