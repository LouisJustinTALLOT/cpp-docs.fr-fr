---
title: "Impossible d’appliquer &#224; la fois &#39;System.STAThreadAttribute&#39; et &#39;System.MTAThreadAttribute&#39; &#224; la m&#234;me m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31512"
  - "bc31512"
helpviewer_keywords: 
  - "BC31512"
ms.assetid: ee27e834-707d-4f02-86d4-831fa9bd2359
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’appliquer &#224; la fois &#39;System.STAThreadAttribute&#39; et &#39;System.MTAThreadAttribute&#39; &#224; la m&#234;me m&#233;thode
Les attributs `System.STAThreadAttribute` et `System.MTAThreadAttribute` s’excluent mutuellement.  
  
 **ID d’erreur :** BC31512  
  
### Pour corriger cette erreur  
  
1.  Appliquez `System.MTAThreadAttribute` ou `System.STAThreadAttribute`, mais pas les deux.  
  
## Voir aussi  
 <xref:System.STAThreadAttribute>   
 <xref:System.MTAThreadAttribute>   
 [NOT IN BUILD : Attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)