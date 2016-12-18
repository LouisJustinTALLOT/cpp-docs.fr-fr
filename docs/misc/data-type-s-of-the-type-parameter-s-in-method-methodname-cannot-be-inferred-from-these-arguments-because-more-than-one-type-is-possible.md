---
title: "Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type dans la m&#233;thode &#39;&lt;nom_m&#233;thode&gt;&#39; &#224; partir de ces arguments, car plusieurs types sont possibles | Microsoft Docs"
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
  - "bc36651"
  - "bc36654"
  - "vbc36651"
  - "vbc36654"
helpviewer_keywords: 
  - "BC36651"
  - "BC36654"
ms.assetid: d4bf408c-ca1f-44ad-855a-3df898de60c6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type dans la m&#233;thode &#39;&lt;nom_m&#233;thode&gt;&#39; &#224; partir de ces arguments, car plusieurs types sont possibles
Impossible de déduire le ou les types de données du ou des paramètres de type dans la méthode '\<nom\_méthode\>' à partir de ces arguments, car plusieurs types sont possibles. La spécification explicite du ou des types de données peut permettre de corriger cette erreur.  
  
 Une tentative a été faite d’utiliser l’inférence de type pour déterminer le ou les types du ou des paramètres de type ou des paramètres dans un appel à une procédure générique. Le compilateur détecte plusieurs types de données possibles pour un ou plusieurs des paramètres de type, et il signale cette erreur.  
  
> [!NOTE]
>  Quand la spécification des arguments n’est pas une option \(par exemple pour les opérateurs de requête dans les expressions de requête\), le message d’erreur apparaît sans la deuxième phrase.  
  
 Le code suivant illustre cette erreur.  
  
```vb#  
Option Strict Off Module Module1 Sub Main() '' Not valid. 'targetMethod(1, "2") End Sub Sub targetMethod(Of T)(ByVal p1 As T, ByVal p2 As T) End Sub End Module  
```  
  
 **ID d’erreur :** BC36654 \(dans les requêtes [!INCLUDE[vbteclinq](../misc/includes/vbteclinq_md.md)]\) et BC36651 \(à l’extérieur de requêtes\)  
  
### Pour corriger cette erreur  
  
-   Si l’erreur s’affiche en dehors d’une requête, essayez de spécifier le type de données du paramètre de type de manière explicite :  
  
    ```  
    targetMethod(Of Integer)(1, "2")  
    ```  
  
## Voir aussi  
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)   
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)