---
title: "Les attributs XML ne peuvent pas &#234;tre s&#233;lectionn&#233;s &#224; partir du type &#39;type&#39;. | Microsoft Docs"
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
  - "bc36808"
  - "vbc36808"
helpviewer_keywords: 
  - "BC36808"
ms.assetid: 76b2605c-3d9b-4e56-ba3f-99c60c668290
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les attributs XML ne peuvent pas &#234;tre s&#233;lectionn&#233;s &#224; partir du type &#39;type&#39;.
Un attribut XML a été référencé pour un objet qui n’est pas de type <xref:System.Xml.Linq.XElement> ou `IEnumerable(Of XElement)`. Pour plus d’informations, consultez [XML Attribute Axis Property](../Topic/XML%20Attribute%20Axis%20Property%20\(Visual%20Basic\).md).  
  
```vb#  
' Generates an error. Dim var = "sample text".@attr  
```  
  
 **ID d’erreur :** BC36808  
  
### Pour corriger cette erreur  
  
-   Vérifiez que l’objet dont vous faites référence à un attribut est fortement typé en tant que <xref:System.Xml.Linq.XElement> ou `IEnumerable(Of XElement)`. Voici un exemple :  
  
    ```vb#  
    Dim elem As XElement = <root attr="value"/> Dim var = elem.@attr  
    ```  
  
## Voir aussi  
 [XML Attribute Axis Property](../Topic/XML%20Attribute%20Axis%20Property%20\(Visual%20Basic\).md)   
 [XML Axis Properties](../Topic/XML%20Axis%20Properties%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)