---
title: "Le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; pour la m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finie dans &#39;&lt;nom_type&gt;&#39; ne peut pas &#234;tre d&#233;duit. | Microsoft Docs"
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
  - "vbc36589"
  - "bc36589"
helpviewer_keywords: 
  - "BC36589"
ms.assetid: 4676a7a5-934b-4b74-b640-48065fc07e94
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le param&#232;tre de type &#39;&lt;nom_param&#232;tre_type&gt;&#39; pour la m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finie dans &#39;&lt;nom_type&gt;&#39; ne peut pas &#234;tre d&#233;duit.
Une méthode d’extension générique est appelée sans fournir de liste d’arguments de type, et l’inférence du type échoue pour l’un des arguments de type.  
  
 Lorsque vous appelez une procédure générique, vous fournissez normalement un argument de type pour chaque paramètre de type défini par la procédure. Toutefois, vous pouvez omettre totalement la liste d’arguments de type. Dans ce cas, le compilateur essaie de déduire le type de chaque argument de type à partir du contexte de votre appel. Pour plus d’informations, consultez « Inférence de type » dans [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md).  
  
 **ID d’erreur :** BC36589  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les types des arguments normaux sont tels que l’inférence du type est cohérente par rapport aux paramètres de type déclarés pour la procédure générique.  
  
     ou  
  
-   Appelez la procédure générique avec une liste d’arguments de type complète pour que l’inférence du type ne soit pas nécessaire.  
  
## Voir aussi  
 [méthodes d'extension.](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [Types génériques Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)