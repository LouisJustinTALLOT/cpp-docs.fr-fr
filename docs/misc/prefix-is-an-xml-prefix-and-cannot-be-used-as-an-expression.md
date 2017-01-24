---
title: "&#39;prefix&#39; est un pr&#233;fixe XML qui ne peut pas &#234;tre utilis&#233; comme expression | Microsoft Docs"
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
  - "bc30114"
  - "vbc30114"
helpviewer_keywords: 
  - "BC30114"
ms.assetid: 5cb7c89e-c61b-483a-9369-5285b7cbcf45
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;prefix&#39; est un pr&#233;fixe XML qui ne peut pas &#234;tre utilis&#233; comme expression
'prefix' est un préfixe XML qui ne peut pas être utilisé comme expression. Utilisez l’opérateur GetXmlNamespace pour créer un objet namespace.  
  
 Le préfixe pour un espace de noms XML importé à l’aide de l’instruction `Imports` ne peut pas être utilisé en dehors d’un littéral XML.  
  
 **ID d’erreur :** BC30114  
  
### Pour corriger cette erreur  
  
-   Si vous devez référencer une partie de l’espace de noms XML importé, utilisez l’opérateur `GetXmlNamespace` pour récupérer un objet <xref:System.Xml.Linq.XNamespace>. Utilisez cet objet à la place du préfixe d’espace de noms XML.  
  
-   Si vous utilisez le préfixe d’espace de noms XML pour qualifier un littéral XML, vérifiez que vous utilisez la syntaxe appropriée pour le littéral XML.  
  
## Voir aussi  
 [XML Literals](../Topic/XML%20Literals%20\(Visual%20Basic\).md)   
 [Imports Statement \(XML Namespace\)](../Topic/Imports%20Statement%20\(XML%20Namespace\).md)   
 [GetXmlNamespace Operator](../Topic/GetXmlNamespace%20Operator%20\(Visual%20Basic\).md)   
 [XML](../Topic/XML%20in%20Visual%20Basic.md)   
 [Introduction to LINQ in Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)