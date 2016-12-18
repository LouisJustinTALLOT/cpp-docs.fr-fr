---
title: "Impossible de convertir les valeurs &#39;Char&#39; en &#39;&lt;nom_type&gt;&#39; | Microsoft Docs"
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
  - "bc32006"
  - "vbc32006"
helpviewer_keywords: 
  - "BC32006"
ms.assetid: c033f65e-a315-47fc-be2e-ed371847a221
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de convertir les valeurs &#39;Char&#39; en &#39;&lt;nom_type&gt;&#39;
Impossible de convertir les valeurs 'Char' en '\<nom\_type\>'. Utilisez soit Microsoft.VisualBasic.AscW pour interpréter un caractère comme une valeur Unicode, soit Microsoft.VisualBasic.Val pour interpréter le caractère comme un chiffre.  
  
 Une expression tente de convertir une valeur `Char` en un type de données autre que `String` ou `Object`.  
  
 **ID d’erreur :** BC32006  
  
### Pour corriger cette erreur  
  
-   Utilisez la fonction `AscW` pour interpréter une valeur `Char` comme un caractère Unicode, ou la fonction `Val` pour l’interpréter comme un chiffre.  
  
## Voir aussi  
 [NOT IN BUILD : Fonctions Asc, AscW](http://msdn.microsoft.com/fr-fr/6814bfec-12ba-41fb-b10e-bec99750d5e1)   
 [NOT IN BUILD : Fonctions Val](http://msdn.microsoft.com/fr-fr/81650f77-9242-4ec1-8e04-e93b5daa451d)   
 [Char Data Type](../Topic/Char%20Data%20Type%20\(Visual%20Basic\).md)