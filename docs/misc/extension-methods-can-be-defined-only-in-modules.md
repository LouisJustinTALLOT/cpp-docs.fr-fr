---
title: "Les m&#233;thodes d’extension ne peuvent &#234;tre d&#233;finies que dans des modules | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36551"
  - "bc36551"
helpviewer_keywords: 
  - "BC36551"
ms.assetid: c832d523-5bf6-4baf-b91c-bd26d94453ed
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les m&#233;thodes d’extension ne peuvent &#234;tre d&#233;finies que dans des modules
Cette erreur se produit lorsqu’une méthode d’extension a été définie en dehors d’un module. En Visual Basic, toutes les méthodes d’extension doivent être définies dans des modules standards.  
  
 **ID d’erreur :** BC36551  
  
### Pour corriger cette erreur  
  
-   Placez la méthode d’extension dans un module.  
  
## Exemple  
 L’exemple suivant étend la classe `String`, en ajoutant une méthode `Print`.  
  
```  
Imports StringUtility Imports System.Runtime.CompilerServices Namespace StringUtility <Extension()> _ Module StringExtensions <Extension()> _ Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub End Module End Namespace  
```  
  
## Voir aussi  
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [méthodes d'extension.](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [Module \<keyword\>](../Topic/Module%20%3Ckeyword%3E%20\(Visual%20Basic\).md)   
 [Module Statement](../Topic/Module%20Statement.md)