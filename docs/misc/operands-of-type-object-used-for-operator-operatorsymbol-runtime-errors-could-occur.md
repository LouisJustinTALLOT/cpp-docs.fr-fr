---
title: "Op&#233;randes de type Object utilis&#233;s pour l’op&#233;rateur &#39;&lt;symbole_op&#233;rateur&gt;&#39;&#160;; des erreurs d’ex&#233;cution peuvent se produire | Microsoft Docs"
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
  - "BC42019"
  - "vbc42019"
helpviewer_keywords: 
  - "BC42019"
ms.assetid: f61944ba-863b-4a82-aae4-249bda52ec8d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Op&#233;randes de type Object utilis&#233;s pour l’op&#233;rateur &#39;&lt;symbole_op&#233;rateur&gt;&#39;&#160;; des erreurs d’ex&#233;cution peuvent se produire
Une expression utilise un opérateur pour lequel un ou deux opérandes sont du [Object Data Type](../Topic/Object%20Data%20Type.md).  
  
 Quand une variable ou une expression prend la valeur `Object`, le compilateur doit exécuter une *liaison tardive*, ce qui entraîne des opérations supplémentaires au moment de l’exécution. Cela expose également votre application à des erreurs d’exécution potentielles. Par exemple, supposez que vous affectez un <xref:System.Windows.Forms.Form> à une variable `Object` et que vous tentez de l’utiliser avec [\/ Operator](../Topic/-%20Operator%20\(Visual%20Basic\)3.md). Si vous procédez ainsi, le runtime lève une <xref:System.InvalidCastException> car Visual Basic ne peut pas convertir un objet <xref:System.Windows.Forms.Form> en valeur numérique.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **ID d’erreur :** BC42019  
  
### Pour corriger cette erreur  
  
-   Si possible, réorganisez les opérandes pour qu’ils correspondent à des types de données pour lesquels l’opérateur est défini.  
  
## Voir aussi  
 [Arithmetic Operators in Visual Basic](../Topic/Arithmetic%20Operators%20in%20Visual%20Basic.md)