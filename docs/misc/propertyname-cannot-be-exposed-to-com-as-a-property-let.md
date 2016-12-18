---
title: "&#39;&lt;nom_propri&#233;t&#233;&gt;&#39; ne peut pas &#234;tre expos&#233; &#224; COM en tant que propri&#233;t&#233; &#39;Let&#39; | Microsoft Docs"
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
  - "bc42102"
  - "vbc42102"
helpviewer_keywords: 
  - "BC42102"
ms.assetid: b77c5b7c-ac43-4b2d-b8bc-582e65e6f7e7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; ne peut pas &#234;tre expos&#233; &#224; COM en tant que propri&#233;t&#233; &#39;Let&#39;
'\<nom\_propriété\>' ne peut pas être exposé à COM en tant que propriété 'Let'. Vous ne serez pas en mesure d’assigner des valeurs qui ne sont pas des objets \(telles que des nombres ou des chaînes\) à cette propriété à partir de Visual Basic 6.0 à l’aide d’une instruction 'Let'.  
  
 Une classe utilisant un bloc d’attributs `COMClassAttribute` déclare une propriété `Public` avec un type de données `Object`. Un programme Visual Basic 6.0 peut accéder à cette propriété en tant que `Variant`, mais il peut uniquement lui affecter une référence d’objet avec l’instruction `Set`. Il ne peut pas assigner un type de valeur avec l’instruction `Let`.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **ID d’erreur :** BC42102  
  
### Pour traiter cet avertissement  
  
-   Songez à contacter les utilisateurs de Visual Basic 6.0 susceptibles d’employer cette classe pour les informer qu’ils ne peuvent pas utiliser cette propriété avec l’instruction `Let`.  
  
## Voir aussi  
 [Default Property Changes in Visual Basic](http://msdn.microsoft.com/fr-fr/9b8cfad7-40ac-4b83-affb-1ff781755a4c)   
 [Property Statement](../Topic/Property%20Statement.md)   
 [Public](../Topic/Public%20\(Visual%20Basic\).md)   
 [Object Data Type](../Topic/Object%20Data%20Type.md)   
 [NOT IN BUILD : Attributs utilisés en Visual Basic](http://msdn.microsoft.com/fr-fr/22231318-8a40-49af-9245-e0aab723563b)   
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute, classe](http://msdn.microsoft.com/fr-fr/5c2f0835-9210-47dc-bc59-5c1769953574)