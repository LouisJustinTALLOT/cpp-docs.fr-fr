---
title: "Impossible d’appliquer &#224; la fois &#39;Microsoft.VisualBasic.ComClassAttribute&#39; et &#39;&lt;attribut&gt;&#39; &#224; la m&#234;me classe | Microsoft Docs"
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
  - "vbc32501"
  - "bc32501"
helpviewer_keywords: 
  - "BC32501"
ms.assetid: dc1bf4f1-f030-4df3-aae8-524af9c2fda7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’appliquer &#224; la fois &#39;Microsoft.VisualBasic.ComClassAttribute&#39; et &#39;&lt;attribut&gt;&#39; &#224; la m&#234;me classe
Un bloc d’attributs `COMClassAttribute` est utilisé conjointement à un attribut qui ne s’applique pas aux objets COM. Les attributs [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)] et COM ont peut\-être été confondus.  
  
 **ID d’erreur :** BC32501  
  
### Pour corriger cette erreur  
  
-   Supprimez le bloc d’attributs `COMClassAttribute` ou l’attribut qui ne s’applique pas à COM.  
  
## Voir aussi  
 [NOT IN BUILD : Attributs utilisés en Visual Basic](http://msdn.microsoft.com/fr-fr/22231318-8a40-49af-9245-e0aab723563b)   
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute, classe](http://msdn.microsoft.com/fr-fr/5c2f0835-9210-47dc-bc59-5c1769953574)