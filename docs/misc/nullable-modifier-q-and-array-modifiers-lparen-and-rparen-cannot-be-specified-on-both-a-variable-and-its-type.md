---
title: "Impossible de sp&#233;cifier le modificateur autorisant les valeurs Null&#160;&#39;?&#39; ainsi que les modificateurs de tableau &#39;(&#39; et &#39;)&#39; pour la variable et son type | Microsoft Docs"
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
  - "vbc33102"
  - "bc33102"
helpviewer_keywords: 
  - "BC33102"
ms.assetid: fd3f65a4-63f9-41dc-ba15-98d86f097ba8
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de sp&#233;cifier le modificateur autorisant les valeurs Null&#160;&#39;?&#39; ainsi que les modificateurs de tableau &#39;(&#39; et &#39;)&#39; pour la variable et son type
Le modificateur de type Nullable \(?\) est inclus dans la variable d’une déclaration de variable dans laquelle les modificateurs de tableau \(parenthèses\) sont inclus dans le type de variable spécifié. Il se peut aussi que le modificateur de type Nullable soit inclus dans le type de variable spécifié d’une déclaration de variable dans laquelle les modificateurs de tableau sont inclus dans la variable.  
  
 **ID d’erreur :** BC33102  
  
### Pour corriger cette erreur  
  
1.  Spécifiez le modificateur de type Nullable \(?\) et les modificateurs de tableau \(parenthèses\) dans la variable déclarée ou le type de variable spécifié, comme indiqué dans l’exemple suivant.  
  
    ```vb#  
    ' These are incorrect. ' Dim numbers? As Integer() ' Dim values() As Integer? 'These are correct. Dim numbers?() As Integer Dim values As Integer?()  
    ```  
  
## Voir aussi  
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)