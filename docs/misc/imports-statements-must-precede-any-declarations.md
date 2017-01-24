---
title: "Des instructions &#39;Imports&#39; doivent pr&#233;c&#233;der toutes les d&#233;clarations | Microsoft Docs"
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
  - "vbc30465"
  - "bc30465"
helpviewer_keywords: 
  - "BC30465"
ms.assetid: 726365f6-d6fc-454a-a43b-afa41bfea82a
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Des instructions &#39;Imports&#39; doivent pr&#233;c&#233;der toutes les d&#233;clarations
Une instruction `Imports` suit une instruction de déclaration dans un fichier source.  
  
 L’instruction `Imports` importe des noms d’espaces de noms à partir de projets et d’assemblys référencés, ainsi que des noms d’espaces de noms définis dans le même projet que celui dans lequel elle apparaît. Les instructions `Imports` doivent être placées dans un fichier source avant les références aux identificateurs.  
  
 **ID d’erreur :** BC30465  
  
### Pour corriger cette erreur  
  
-   Déplacez l’instruction `Imports` en haut du fichier source, avant les instructions de déclaration.  
  
## Voir aussi  
 [Imports Statement \(.NET Namespace and Type\)](../Topic/Imports%20Statement%20\(.NET%20Namespace%20and%20Type\).md)