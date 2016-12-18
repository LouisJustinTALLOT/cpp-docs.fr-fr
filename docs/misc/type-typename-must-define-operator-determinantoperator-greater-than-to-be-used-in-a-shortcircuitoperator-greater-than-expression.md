---
title: "Le type &#39;&lt;nom_type&gt;&#39; doit d&#233;finir l’op&#233;rateur &#39;&lt;op&#233;rateur_d&#233;terminant&gt;&#39; &#224; utiliser dans une expression &#39;&lt;op&#233;rateur_court-circuit&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33035"
  - "vbc33035"
helpviewer_keywords: 
  - "BC33035"
ms.assetid: 50a0a39f-63cd-4100-aea9-91b5b6ab5bbf
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type &#39;&lt;nom_type&gt;&#39; doit d&#233;finir l’op&#233;rateur &#39;&lt;op&#233;rateur_d&#233;terminant&gt;&#39; &#224; utiliser dans une expression &#39;&lt;op&#233;rateur_court-circuit&gt;&#39;
Un [AndAlso Operator](../Topic/AndAlso%20Operator%20\(Visual%20Basic\).md) ou un [OrElse Operator](../Topic/OrElse%20Operator%20\(Visual%20Basic\).md) utilise des opérandes d’un type de classe ou de structure quand cette classe ou structure ne définit pas un opérateur obligatoire.  
  
 Sachant que vous ne définissez pas directement un opérateur de court\-circuit \(`AndAlso` ou `OrElse`\), vous devez définir les opérateurs logiques et déterminants correspondants. Le tableau suivant présente les opérateurs obligatoires.  
  
|Opérateur de court\-circuit|Opérateur logique|Opérateur déterminant|  
|---------------------------------|-----------------------|---------------------------|  
|`AndAlso`|[And Operator](../Topic/And%20Operator%20\(Visual%20Basic\).md)|[IsFalse Operator](../Topic/IsFalse%20Operator%20\(Visual%20Basic\).md)|  
|`OrElse`|[Or Operator](../Topic/Or%20Operator%20\(Visual%20Basic\).md)|[IsTrue Operator](../Topic/IsTrue%20Operator%20\(Visual%20Basic\).md)|  
  
 [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] utilise ces opérateurs logiques et déterminants pour construire la logique de court\-circuit pour `AndAlso` ou `OrElse`. Pour que cela fonctionne correctement, les opérandes et la valeur de retour de votre définition de `And` ou `Or` doivent être du type conteneur, c’est\-à\-dire, du type de la classe ou de la structure dans laquelle vous définissez `And` ou `Or`.  
  
 **ID d’erreur :** BC33035  
  
### Pour corriger cette erreur  
  
-   Définissez les opérateurs `And` et `IsFalse` ou les opérateurs `Or` et `IsTrue` dans la classe ou la structure utilisée pour le type d’opérande de l’opérateur `AndAlso` ou `OrElse`. Vérifiez que les opérandes pour `And` ou `Or` sont du type de la classe ou de la structure dans laquelle vous le définissez.  
  
## Voir aussi  
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Logical and Bitwise Operators in Visual Basic](../Topic/Logical%20and%20Bitwise%20Operators%20in%20Visual%20Basic.md)