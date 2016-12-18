---
title: "La variable de contr&#244;le de boucle &#39;For&#39; ne peut pas &#234;tre de type &#39;&lt;type&gt;&#39; | Microsoft Docs"
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
  - "vbc30337"
  - "bc30337"
helpviewer_keywords: 
  - "BC30337"
ms.assetid: 988bba15-e9a2-4045-98a0-7f53c8b2c3e3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable de contr&#244;le de boucle &#39;For&#39; ne peut pas &#234;tre de type &#39;&lt;type&gt;&#39;
Vous avez tenté d’utiliser une variable de contrôle de boucle qui n’est pas du type valide. Au début d’une boucle `For`, le point de départ, le point de terminaison et la valeur de pas sont évalués dans l’ordre textuel. Les trois expressions doivent toutes être implicitement convertibles en type de la variable. Si la variable de boucle `For` est de type `Object`, alors au moins une des expressions au moment de l’exécution doit être de type numérique et les trois expressions doivent toutes pouvoir être forcées au type numérique le plus large parmi elles.  
  
 **ID d’erreur :** BC30337  
  
### Pour corriger cette erreur  
  
-   Vérifiez le type de la variable de contrôle de boucle et remplacez\-le par un type valide.  
  
## Voir aussi  
 [For \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/c470a263-9b49-4308-8fd6-8592b84a7980)   
 [Do...Loop Statement](../Topic/Do...Loop%20Statement%20\(Visual%20Basic\).md)   
 [For...Next, instruction](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)