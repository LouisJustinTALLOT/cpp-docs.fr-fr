---
title: "Property Get/Let/Set ne sont plus pris en charge&#160;; utilisez la nouvelle syntaxe de d&#233;claration Property. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30808"
  - "bc30808"
helpviewer_keywords: 
  - "BC30808"
ms.assetid: c8a803eb-316d-4f73-b6ef-27a2914409f3
caps.latest.revision: 10
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Property Get/Let/Set ne sont plus pris en charge&#160;; utilisez la nouvelle syntaxe de d&#233;claration Property.
`Property Get/Let/Set` ne sont plus pris en charge ; utilisez la nouvelle syntaxe de déclaration `Property`.  
  
 La syntaxe de déclaration des propriétés a changé. Celles\-ci sont définies à présent à l’intérieur des blocs.  
  
 **ID d’erreur :** BC30808  
  
### Pour corriger cette erreur  
  
1.  Définissez les propriétés dans des blocs de code commençant par le mot clé `Property`. Terminez les propriétés en utilisant la construction `End Property`.  
  
2.  Définissez les procédures de propriété `Get` à l’intérieur des blocs de propriété à l’aide du mot clé `Get`. Terminez les procédures de propriété `Get` par la construction `End Get`.  
  
3.  Définissez les procédures de propriété `Set` à l’intérieur des blocs de propriété à l’aide du mot clé `Set`. Terminez les procédures de propriété `Set` par la construction `End Set`.  
  
4.  Utilisez les procédures de propriété `Set` pour toutes les assignations de propriétés. Les procédures de propriété `Let` ne sont plus nécessaires ni prises en charge.  
  
## Voir aussi  
 [Property Statement](../Topic/Property%20Statement.md)   
 [Language Changes in Visual Basic](http://msdn.microsoft.com/fr-fr/a1be4461-a0e4-4a88-a32c-dcad41ed119a)