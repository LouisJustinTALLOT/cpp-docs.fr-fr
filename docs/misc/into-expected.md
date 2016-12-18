---
title: "&#39;Into&#39; attendu | Microsoft Docs"
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
  - "bc36615"
  - "vbc36615"
helpviewer_keywords: 
  - "BC36615"
ms.assetid: 24062dd9-a973-43b6-88d3-c11adc5a3736
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Into&#39; attendu
Vous avez spécifié une clause `Aggregate`, `Group By` ou `Group Join` sans opérateur `Into`. Vous utilisez l’opérateur `Into` pour identifier des fonctions d’agrégation à appliquer au résultat de la requête et pour identifier le membre du type de résultat de requête où stocker les résultats groupés \(à l’aide de la fonction d’agrégation `Group`\).  
  
 **ID d’erreur :** BC36615  
  
### Pour corriger cette erreur  
  
1.  Ajoutez l’opérateur `Into` à la clause `Aggregate`, `Group By` ou `Group Join`. Voici un exemple :  
  
    ```vb#  
    Dim orders = From order In orderList _ Order By order.OrderDate _ Group By OrderDate = order.OrderDate _ Into OrdersByDate = Group  
    ```  
  
## Voir aussi  
 [Aggregate Clause](../Topic/Aggregate%20Clause%20\(Visual%20Basic\).md)   
 [Group By, clause](../Topic/Group%20By%20Clause%20\(Visual%20Basic\).md)   
 [Group Join Clause](../Topic/Group%20Join%20Clause%20\(Visual%20Basic\).md)   
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)