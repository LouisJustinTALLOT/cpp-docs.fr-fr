---
title: "Litt&#233;raux XML et propri&#233;t&#233;s d’axe XML non disponibles | Microsoft Docs"
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
  - "bc31190"
  - "vbc31190"
helpviewer_keywords: 
  - "BC31190"
ms.assetid: cb861748-0ee4-40d3-a859-98ca6c39b4f4
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Litt&#233;raux XML et propri&#233;t&#233;s d’axe XML non disponibles
Les littéraux XML et les propriétés d’axe XML ne sont pas disponibles. Ajoutez des références à System.Xml, System.Xml.Linq et System.Core.  
  
 Le code compilé inclut des littéraux XML ou des propriétés d’axe XML, mais il ne référence pas les assemblys nécessaires à la compilation des littéraux XML ou propriétés d’axe XML.  
  
 **ID d’erreur :** BC31190  
  
### Pour corriger cette erreur  
  
-   Ajoutez des références aux assemblys System.Xml.dll, System.Xml.Linq.dll etSystem.Core.dll.  
  
## Voir aussi  
 [XML Literals](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [XML Axis Properties](../Topic/XML%20Axis%20Properties%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)