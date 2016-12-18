---
title: "La classe &#39;&lt;nom_classe&gt;&#39; doit d&#233;clarer un &#39;Sub New&#39;, car le &#39;&lt;nom_constructeur&gt;&#39; dans sa classe de base &#39;&lt;nom_classe_de_base&gt;&#39; est marqu&#233; comme obsol&#232;te | Microsoft Docs"
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
  - "vbc30917"
  - "bc30917"
helpviewer_keywords: 
  - "BC30917"
ms.assetid: 764d222d-e058-40ad-a354-29b956a8027b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La classe &#39;&lt;nom_classe&gt;&#39; doit d&#233;clarer un &#39;Sub New&#39;, car le &#39;&lt;nom_constructeur&gt;&#39; dans sa classe de base &#39;&lt;nom_classe_de_base&gt;&#39; est marqu&#233; comme obsol&#232;te
Une déclaration de classe ne contient pas de constructeur, et le constructeur de classe de base est marqué avec l’attribut <xref:System.ObsoleteAttribute> et la directive pour la traiter en tant qu’erreur.  
  
 Lorsqu’une classe dérivée ne déclare pas de constructeur, [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] tente de générer un constructeur sans paramètre implicite qui appelle `MyBase.New()`. S’il n’existe aucun constructeur accessible dans la classe de base qui peut être appelé sans arguments, [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] ne peut pas générer de constructeur implicite. Dans ce cas, le constructeur nécessaire est marqué avec l’attribut <xref:System.ObsoleteAttribute>, et [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] ne peut pas l’appeler.  
  
 Vous pouvez marquer un élément de programmation comme n’étant plus utilisé en lui appliquant <xref:System.ObsoleteAttribute>. Si vous procédez ainsi, vous pouvez affecter la valeur `True` ou `False` à la propriété <xref:System.ObsoleteAttribute.IsError%2A> de l’attribut. Si vous lui affectez la valeur `True`, le compilateur traite toute tentative d’utilisation de l’élément comme une erreur. Si vous lui affectez la valeur `False`, ou si vous conservez la valeur par défaut `False`, le compilateur émet un avertissement en cas de tentative d’utilisation de l’élément.  
  
 **ID d’erreur :** BC30917  
  
### Pour corriger cette erreur  
  
-   Utilisez `Sub New` pour déclarer un constructeur dans la classe dérivée.  
  
## Voir aussi  
 [NOT IN BUILD : Attributs utilisés en Visual Basic](http://msdn.microsoft.com/fr-fr/22231318-8a40-49af-9245-e0aab723563b)   
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)