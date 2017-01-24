---
title: "La contrainte &#39;&lt;contrainte1&gt;&#39; est en conflit avec la contrainte indirecte &#39;&lt;contrainte2&gt;&#39; obtenue de la contrainte de param&#232;tre de type &#39;&lt;param&#232;tre_de_type1&gt;&#39;. | Microsoft Docs"
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
  - "bc32110"
  - "vbc32110"
helpviewer_keywords: 
  - "BC32110"
ms.assetid: e799214d-23b4-4a3f-b61a-0b9d3387ead3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La contrainte &#39;&lt;contrainte1&gt;&#39; est en conflit avec la contrainte indirecte &#39;&lt;contrainte2&gt;&#39; obtenue de la contrainte de param&#232;tre de type &#39;&lt;param&#232;tre_de_type1&gt;&#39;.
Un type générique est déclaré avec des contraintes en conflit en raison d’une combinaison de contraintes directes et indirectes.  
  
 L’instruction suivante peut générer cette erreur.  
  
 `Public Class testClass(Of t1 As {Structure, t2}, t2 As Class)`  
  
 La contrainte directe `Structure` et la contrainte indirecte `Class` provoquent un conflit pour le paramètre de type `t1`, car la contrainte `Structure` exige que l’argument de type correspondant soit un type valeur, alors que `Class` exige qu’il soit un type référence.  
  
 **ID d’erreur :** BC32110  
  
### Pour corriger cette erreur  
  
-   Modifiez les contraintes de paramètre de type pour éviter les conflits entre contraintes.  
  
## Voir aussi  
 [Types génériques Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)   
 [Structure \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Classe \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)