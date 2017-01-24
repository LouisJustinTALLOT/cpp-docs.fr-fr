---
title: "Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type &#224; partir de ces arguments, car plusieurs types sont possibles | Microsoft Docs"
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
  - "vbc36653"
  - "bc36653"
  - "vbc36650"
  - "bc36650"
helpviewer_keywords: 
  - "BC36650"
  - "BC36653"
ms.assetid: 79287e1f-7070-4a71-96d2-aee0a0c9d8bd
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type &#224; partir de ces arguments, car plusieurs types sont possibles
Impossible de déduire le ou les types de données du ou des paramètres de type à partir de ces arguments, car plusieurs types sont possibles. La spécification explicite du ou des types de données peut permettre de corriger cette erreur.  
  
 Cette erreur se produit lorsque la résolution de surcharge a échoué. Elle entraîne l’affichage d’un message subordonné qui indique pourquoi un candidat de surcharge particulier a été éliminé. L’erreur explique que si l’inférence de type est appliquée pour déterminer le type de données des paramètres de type de la procédure générique appelée, le compilateur détecte plusieurs types de données possibles pour au moins l’un d’entre eux.  
  
> [!NOTE]
>  Quand la spécification des arguments n’est pas une option \(par exemple pour les opérateurs de requête dans les expressions de requête\), le message d’erreur apparaît sans la deuxième phrase.  
  
 Pour plus d’informations et d’exemples, consultez [Impossible de déduire le ou les types de données du ou des paramètres de type dans la méthode '\<nom\_méthode\>' à partir de ces arguments, car plusieurs types sont possibles](../misc/data-type-s-of-the-type-parameter-s-in-method-methodname-cannot-be-inferred-from-these-arguments-because-more-than-one-type-is-possible.md).  
  
 **ID d’erreur :** BC36653 et BC36650  
  
## Voir aussi  
 [Generic Procedures in Visual Basic](../Topic/Generic%20Procedures%20in%20Visual%20Basic.md)   
 [Overload Resolution](../Topic/Overload%20Resolution%20\(Visual%20Basic\).md)