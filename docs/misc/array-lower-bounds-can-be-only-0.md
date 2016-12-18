---
title: "Les limites inf&#233;rieures du tableau ne peuvent &#234;tre que&#160;&#39;0&#39; | Microsoft Docs"
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
  - "bc32059"
  - "vbc32059"
helpviewer_keywords: 
  - "BC32059"
ms.assetid: 273b69df-910e-45d2-acac-632005d24c5a
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les limites inf&#233;rieures du tableau ne peuvent &#234;tre que&#160;&#39;0&#39;
Une instruction de déclaration ou une clause `New` spécifie un tableau avec une limite inférieure différente de 0.  
  
 Quand vous créez ou initialisez une variable tableau, vous pouvez éventuellement spécifier la limite supérieure de chaque dimension. Dans ce cas, la longueur de cette dimension devient la limite supérieure plus un, car la limite inférieure est toujours égale à zéro. Vous pouvez éventuellement spécifier la limite inférieure, mais vous devez spécifier 0. Grâce à cette approche, votre code est plus facile à lire.  
  
 **ID d’erreur :** BC32059  
  
### Pour corriger cette erreur  
  
-   Affectez à la spécification de la limite inférieure la valeur 0 ou supprimez\-la entièrement.  
  
## Voir aussi  
 [Tableaux](../Topic/Arrays%20in%20Visual%20Basic.md)   
 [NOTINBUILD Comment : spécifier une limite inférieure de zéro sur un tableau](http://msdn.microsoft.com/fr-fr/20ffd49a-64f7-4634-8ed0-46ba1049d935)