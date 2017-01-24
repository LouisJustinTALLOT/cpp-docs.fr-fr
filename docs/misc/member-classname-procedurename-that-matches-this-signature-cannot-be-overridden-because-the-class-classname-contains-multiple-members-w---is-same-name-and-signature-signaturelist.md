---
title: "Le membre &#39;&lt;nom_classe&gt;.&lt;nom_proc&#233;dure&gt;&#39; qui correspond &#224; cette signature ne peut pas &#234;tre remplac&#233;, car la classe &#39;&lt;nom_classe&gt;&#39; contient plusieurs membres avec ce nom et cette signature&#160;: &lt;liste_signatures&gt; | Microsoft Docs"
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
  - "bc30935"
  - "vbc30935"
helpviewer_keywords: 
  - "BC30935"
ms.assetid: 1165b630-668d-417d-9e18-9b8ffe7f6980
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le membre &#39;&lt;nom_classe&gt;.&lt;nom_proc&#233;dure&gt;&#39; qui correspond &#224; cette signature ne peut pas &#234;tre remplac&#233;, car la classe &#39;&lt;nom_classe&gt;&#39; contient plusieurs membres avec ce nom et cette signature&#160;: &lt;liste_signatures&gt;
Une procédure ou une propriété tente de substituer une procédure ou une propriété héritée, mais le compilateur détecte plusieurs versions de la procédure ou de la propriété de base avec le même nom et la même signature.  
  
 Cette erreur peut se produire avec les types génériques construits, comme l’illustrent les déclarations suivantes.  
  
```  
Public Class baseClass(Of t) Public Overridable Sub doSomething(ByVal inputValue As String) End Sub Public Overridable Sub doSomething(ByVal inputValue As t) End Sub End Class Public Class derivedClass Inherits baseClass(Of String) Overrides Sub doSomething(ByVal inputValue As String) End Sub End Class  
```  
  
 Étant donné que `derivedClass` hérite de `baseClass` qui fournit `String` à son paramètre de type `t`, les deux versions de `doSomething` dans `baseClass` assument des signatures identiques aux yeux de `derivedClass`. Ainsi, le compilateur ne peut pas déterminer la version à substituer.  
  
 **ID d’erreur :** BC30935  
  
### Pour corriger cette erreur  
  
-   Modifiez le ou les arguments de type que vous fournissez à la classe de base pour qu’elle ne provoque pas l’existence d’une ou plusieurs signatures identiques des procédures ou propriétés membres.  
  
     ou  
  
-   Si vous devez hériter de la classe de base avec le jeu d’arguments de type que vous utilisez, ne substituez pas la procédure ou la propriété mentionnée dans ce message d’erreur.  
  
## Voir aussi  
 [Overridable](../Topic/Overridable%20\(Visual%20Basic\).md)   
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)