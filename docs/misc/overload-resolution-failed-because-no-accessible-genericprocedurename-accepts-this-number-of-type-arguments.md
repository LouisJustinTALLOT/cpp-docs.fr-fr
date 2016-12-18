---
title: "La r&#233;solution de surcharge a &#233;chou&#233;, car aucun &#39;&lt;nom_proc&#233;dure_g&#233;n&#233;rique&gt;&#39; accessible n’accepte ce nombre d’arguments de type | Microsoft Docs"
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
  - "bc32087"
  - "vbc32087"
helpviewer_keywords: 
  - "BC32087"
ms.assetid: a3eaafd3-80f6-4b7d-9b75-47b043fe17b5
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La r&#233;solution de surcharge a &#233;chou&#233;, car aucun &#39;&lt;nom_proc&#233;dure_g&#233;n&#233;rique&gt;&#39; accessible n’accepte ce nombre d’arguments de type
Un appel à une procédure générique surchargée ne peut pas être résolu, car le compilateur ne peut pas accéder à une version surchargée avec le nombre approprié de paramètres de type.  
  
 Quand vous appelez une procédure générique, vous devez fournir un argument de type pour chaque paramètre de type. Vous pouvez également ne fournir aucun argument de type et laisser le compilateur effectuer une *inférence de type*. Pour plus d’informations, consultez « Inférence de type » dans [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md).  
  
 **ID d’erreur :** BC32087  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que la version que vous comptez appeler est accessible par le code appelant. Consultez [Access Levels in Visual Basic](../Topic/Access%20Levels%20in%20Visual%20Basic.md).  
  
2.  Ajoutez ou supprimez des arguments de type dans votre code appelant pour que la liste d’arguments de type corresponde à la liste de paramètres de type de la version que vous voulez appeler.  
  
     ou  
  
     Supprimez tous les arguments de type de votre code appelant et laissez le compilateur tenter d’effectuer une inférence de type. N’oubliez pas que l’inférence de type peut échouer en cas de conflits ou d’ambiguïtés.  
  
## Voir aussi  
 [Overloaded Properties and Methods](../Topic/Overloaded%20Properties%20and%20Methods%20\(Visual%20Basic\).md)   
 [Overload Resolution](../Topic/Overload%20Resolution%20\(Visual%20Basic\).md)   
 [Types génériques Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)