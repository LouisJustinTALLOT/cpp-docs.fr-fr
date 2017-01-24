---
title: "La m&#233;thode &#39;&lt;nom_m&#233;thode&gt;&#39; n’a pas la m&#234;me signature que le d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39; | Microsoft Docs"
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
  - "bc30408"
  - "vbc30408"
helpviewer_keywords: 
  - "BC30408"
ms.assetid: 845f6686-388f-4253-b635-146e517015a1
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La m&#233;thode &#39;&lt;nom_m&#233;thode&gt;&#39; n’a pas la m&#234;me signature que le d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39;
Il existe une incompatibilité entre les signatures de la méthode et du délégué que vous essayez d’utiliser. L’instruction `Delegate` définit les types de paramètre et les types de retour d’une classe déléguée. Toute procédure ayant des paramètres, des types et un type de retour correspondants peut être utilisée pour créer une instance de ce type de délégué. Chaque classe déléguée définit un constructeur auquel les caractéristiques d’une méthode objet sont passées.  
  
 **ID d’erreur :** BC30408  
  
### Pour corriger cette erreur  
  
-   Vérifiez les signatures pour trouver l’incompatibilité et corrigez\-la.  
  
## Voir aussi  
 [Delegate Statement](../Topic/Delegate%20Statement.md)