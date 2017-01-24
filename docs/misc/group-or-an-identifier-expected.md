---
title: "&#39;Group&#39; ou identificateur attendu | Microsoft Docs"
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
  - "vbc36707"
  - "bc36707"
helpviewer_keywords: 
  - "BC36707"
ms.assetid: 214e4aa3-d20f-41b3-902c-f1076d31b832
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Group&#39; ou identificateur attendu
La partie `Into` d’une clause `Group By` ou `Group Join` n’inclut pas le mot clé `Group`. Vous devez inclure le mot clé `Group` dans la clause `Into` d’une clause `Group By` ou `Group Join` pour identifier le nom de la variable à utiliser pour les résultats groupés. Cela peut être un nom que vous spécifiez ou le mot clé `Group`.  
  
 **ID d’erreur :** BC36707  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que la partie `Into` de la clause `Group By` ou `Group Join` inclut le mot clé `Group`, comme indiqué dans l’exemple suivant.  
  
    ```vb#  
    Dim orders = From order In orderList _ Order By order.OrderDate _ Group By OrderDate = order.OrderDate _ Into OrdersByDate = Group  
    ```  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [Group By, clause](../Topic/Group%20By%20Clause%20\(Visual%20Basic\).md)   
 [Group Join Clause](../Topic/Group%20Join%20Clause%20\(Visual%20Basic\).md)