---
title: "Impossible d’impl&#233;menter l’interface &#39;&lt;nom_interface1&gt;&#39;, car son impl&#233;mentation pourrait &#234;tre en conflit avec l’impl&#233;mentation d’une autre interface &#39;&lt;nom_interface2&gt;&#39; impl&#233;ment&#233;e pour certains arguments de type | Microsoft Docs"
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
  - "BC32072"
  - "vbc32072"
helpviewer_keywords: 
  - "BC32072"
ms.assetid: af1cc688-c8cf-4cb2-a8a9-310f5139fe7b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’impl&#233;menter l’interface &#39;&lt;nom_interface1&gt;&#39;, car son impl&#233;mentation pourrait &#234;tre en conflit avec l’impl&#233;mentation d’une autre interface &#39;&lt;nom_interface2&gt;&#39; impl&#233;ment&#233;e pour certains arguments de type
Une déclaration de classe inclut une instruction `Implements` qui spécifie plusieurs interfaces. Or, au moins une des interfaces est générique et deux des implémentations pourraient entrer en conflit pour certaines valeurs d’arguments de type.  
  
 Les instructions suivantes peuvent générer cette erreur.  
  
```  
Public Interface iFace1 Sub testSub(ByVal arg As String) End Interface Public Interface iFace2(Of t) Sub testSub(ByVal arg As t) End Interface Public Class testClass Implements iFace1, iFace2(Of String) End Class  
```  
  
 Sachant que `iFace2` est construit en utilisant `String`, `testClass` doit implémenter deux versions de `testSub` avec des signatures identiques. Cela crée une ambiguïté quant à la version à laquelle accéder.  
  
 **ID d’erreur :** BC32072  
  
### Pour corriger cette erreur  
  
-   Modifiez l’argument de type fourni à l’interface générique pour éviter tout conflit.  
  
     ou  
  
-   Supprimez de l’instruction `Implements` l’une des interfaces provoquant le conflit d’implémentation.  
  
## Voir aussi  
 [Class Statement](../Topic/Class%20Statement%20\(Visual%20Basic\).md)   
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)   
 [Implements Statement](../Topic/Implements%20Statement.md)   
 [NOT IN BUILD : Implements, mot clé et instruction](http://msdn.microsoft.com/fr-fr/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Types génériques Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)