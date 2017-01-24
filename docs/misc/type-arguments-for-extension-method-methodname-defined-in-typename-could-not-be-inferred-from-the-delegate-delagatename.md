---
title: "Les arguments de type pour la m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finis dans &#39;&lt;nom_type&gt;&#39; n’ont pas pu &#234;tre d&#233;duits &#224; partir du d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36581"
  - "vbc36581"
helpviewer_keywords: 
  - "BC36581"
ms.assetid: 2bb9ca8d-7293-40e9-9285-e20b8254b3af
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les arguments de type pour la m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finis dans &#39;&lt;nom_type&gt;&#39; n’ont pas pu &#234;tre d&#233;duits &#224; partir du d&#233;l&#233;gu&#233; &#39;&lt;nom_d&#233;l&#233;gu&#233;&gt;&#39;
Une instruction d’assignation utilise `AddressOf` pour assigner l’adresse d’une méthode d’extension générique à un délégué, mais elle ne fournit pas d’arguments de type à la méthode d’extension.  
  
 En général, quand vous appelez une méthode générique, vous fournissez un argument de type pour chaque paramètre de type défini par la méthode générique. Si vous ne fournissez pas d’arguments de type, le compilateur tente de déduire les types à passer aux paramètres de type. Si le contexte ne fournit pas au compilateur des informations suffisantes pour déduire les types, une erreur est générée.  
  
 **ID d’erreur :** BC36581  
  
### Pour corriger cette erreur  
  
-   Dans l’expression `AddressOf`, spécifiez les arguments de type pour la méthode d’extension.  
  
## Voir aussi  
 [Types génériques Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [AddressOf Operator](../Topic/AddressOf%20Operator%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [méthodes d'extension.](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)