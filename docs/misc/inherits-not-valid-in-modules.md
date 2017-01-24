---
title: "&#39;Inherits&#39; n’est pas valide dans les modules | Microsoft Docs"
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
  - "vbc30230"
  - "bc30230"
helpviewer_keywords: 
  - "BC30230"
ms.assetid: bccd61f7-cb47-4101-9b35-743c97876630
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Inherits&#39; n’est pas valide dans les modules
Une instruction `Inherits` se produit à l’intérieur un module. Les modules ne peuvent pas hériter de classes.  
  
 **ID d’erreur :** BC30230  
  
### Pour corriger cette erreur  
  
-   Supprimez l’instruction `Inherits` ou retapez le module en tant que classe.  
  
## Voir aussi  
 [Inherits Statement](../Topic/Inherits%20Statement.md)   
 [Module Statement](../Topic/Module%20Statement.md)