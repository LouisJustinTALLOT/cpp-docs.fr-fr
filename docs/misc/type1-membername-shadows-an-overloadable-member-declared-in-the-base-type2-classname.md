---
title: "&lt;type1&gt; &#39;&lt;nom_membre&gt;&#39; masque un membre surchargeable d&#233;clar&#233; dans &lt;type2&gt; &#39;&lt;nom_classe&gt;&#39; de base | Microsoft Docs"
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
  - "bc40003"
  - "vbc40003"
helpviewer_keywords: 
  - "BC40003"
ms.assetid: 1e0d2061-0ad9-4915-b946-d55cb5d5ee80
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt; &#39;&lt;nom_membre&gt;&#39; masque un membre surchargeable d&#233;clar&#233; dans &lt;type2&gt; &#39;&lt;nom_classe&gt;&#39; de base
\<type1\> '\<nom\_membre\>' masque un membre surchargeable déclaré dans \<type2\> '\<nom\_classe\>' de base. Si vous souhaitez surcharger la méthode de base, vous devez déclarer cette méthode 'Overloads'.  
  
 Une classe dérivée définit une procédure `Function` ou `Sub`, ou `Property` avec le même nom qu’une procédure ou propriété définie dans la classe de base. Étant donné que les procédures et les propriétés sont des membres surchargeables, la classe dérivée peut surcharger ou masquer le membre de la classe de base. Toutefois, le code de la classe dérivée ne spécifie ni [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) ni [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md) dans la déclaration. En l’absence de l’un ou l’autre des mots clés, le compilateur suppose `Shadows`.  
  
 En programmation, il est conseillé de spécifier `Overloads` ou `Shadows`. Cela rend votre code plus lisible et plus compréhensible.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **ID d’erreur :** BC40003  
  
### Pour corriger cette erreur  
  
-   Si vous souhaitez surcharger la méthode ou la propriété de la classe de base, incluez le mot clé `Overloads` dans la déclaration.  
  
-   Si vous souhaitez masquer la méthode ou la propriété de la classe de base, incluez le mot clé `Shadows` à la place de `Overloads`.  
  
-   Si vous ne souhaitez ni surcharger ni masquer le membre de la classe de base, modifiez le nom du membre de la classe dérivée.  
  
## Voir aussi  
 [Procedure Overloading](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)   
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)   
 [Shadowing in Visual Basic](../Topic/Shadowing%20in%20Visual%20Basic.md)   
 [Function Statement](../Topic/Function%20Statement%20\(Visual%20Basic\).md)   
 [Sub Statement](../Topic/Sub%20Statement%20\(Visual%20Basic\).md)   
 [Property Statement](../Topic/Property%20Statement.md)