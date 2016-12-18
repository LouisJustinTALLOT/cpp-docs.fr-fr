---
title: "Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type dans la m&#233;thode &#39;&lt;nom_m&#233;thode&gt;&#39; &#224; partir de ces arguments, car ils ne sont pas convertis vers le m&#234;me type | Microsoft Docs"
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
  - "vbc36660"
  - "bc36660"
  - "vbc36657"
  - "bc36657"
helpviewer_keywords: 
  - "BC36660"
  - "BC36660"
ms.assetid: e80c5afd-e16d-4f03-bdf1-c79c4286114b
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type dans la m&#233;thode &#39;&lt;nom_m&#233;thode&gt;&#39; &#224; partir de ces arguments, car ils ne sont pas convertis vers le m&#234;me type
Impossible de déduire le ou les types de données du ou des paramètres de type dans la méthode '\<nom\_méthode\>' à partir de ces arguments, car ils ne sont pas convertis vers le même type. La spécification explicite du ou des types de données peut permettre de corriger cette erreur.  
  
 Une tentative a été faite d’utiliser l’inférence de type pour déterminer le ou les types de données du ou des paramètres de type pendant l’évaluation d’un appel à une procédure générique. Le compilateur n’a pas pu trouver un type de données qui satisfasse aux contraintes de tous les arguments. Par conséquent, il a signalé cette erreur.  
  
> [!NOTE]
>  Quand la spécification d’arguments n’est pas une option \(par exemple, pour les opérateurs de requête dans les expressions de requête\), le message d’erreur apparaît sans la deuxième phrase.  
  
 Le code suivant illustre cette erreur.  
  
```vb#  
Option Strict Off Module Module1 Sub Main() '' Not valid. Integer and Date do not convert to the same type. 'targetMethod(19, #3/4/2007#) End Sub Sub targetMethod(Of T)(ByVal p1 As T, ByVal p2 As T) End Sub End Module  
```  
  
 **ID d’erreur :** BC36660 et BC36657  
  
### Pour corriger cette erreur  
  
-   Vous pourrez peut\-être convertir explicitement un ou plusieurs arguments en type compatible, comme le montre le code suivant :  
  
    ```  
    targetMethod(19, #3/4/2007#.ToOADate)  
    ```  
  
-   Vous pourrez peut\-être spécifier un type de données pour le ou les paramètres de type dans lesquels les arguments se convertissent, comme le montre le code suivant :  
  
    ```  
    targetMethod(Of String)(19, #3/4/2007#)  
    ```  
  
## Voir aussi  
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Type Conversion Functions](../Topic/Type%20Conversion%20Functions%20\(Visual%20Basic\).md)   
 [Implicit and Explicit Conversions](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md)   
 [Type Conversions in Visual Basic](../Topic/Type%20Conversions%20in%20Visual%20Basic.md)