---
title: "La constante &#39;&lt;nom_constante&gt;&#39; ne peut pas d&#233;pendre de sa propre valeur | Microsoft Docs"
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
  - "bc30500"
  - "vbc30500"
helpviewer_keywords: 
  - "BC30500"
ms.assetid: 0dad89bc-9196-492f-acd9-7777757362f7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La constante &#39;&lt;nom_constante&gt;&#39; ne peut pas d&#233;pendre de sa propre valeur
Vous avez créé une dépendance circulaire dans votre code, où une constante dépend de sa propre valeur. Par exemple, `Const a = Const b; Const b = Const a`.  
  
 **ID d’erreur :** BC30500  
  
### Pour corriger cette erreur  
  
1.  Vérifiez votre code pour déterminer où la constante est évaluée, puis modifiez\-le en conséquence.  
  
## Voir aussi  
 [NOTINBUILD Vue d’ensemble des constantes](http://msdn.microsoft.com/fr-fr/5c7f57fb-48b2-4a2f-afee-79d8e3adf15b)