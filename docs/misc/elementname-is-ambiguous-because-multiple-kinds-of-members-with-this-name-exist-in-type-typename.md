---
title: "&#39;&lt;nom_&#233;l&#233;ment&gt;&#39; est ambigu, car plusieurs genres de membres portant ce nom existent dans &lt;type&gt; &#39;&lt;nom_type&gt;&#39; | Microsoft Docs"
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
  - "bc31429"
  - "vbc31429"
helpviewer_keywords: 
  - "BC31429"
ms.assetid: fdc92c16-934d-47c0-9c44-332cbd58b73b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_&#233;l&#233;ment&gt;&#39; est ambigu, car plusieurs genres de membres portant ce nom existent dans &lt;type&gt; &#39;&lt;nom_type&gt;&#39;
Une expression accède à un élément de programmation défini dans une classe, une structure, un module ou une interface qui contient plusieurs membres portant le même nom.  
  
 Le *respect de la casse* est probablement à l’origine de cette erreur. Les noms Visual Basic ne respectent pas la casse, ce qui signifie que vous pouvez les capitaliser différemment à différents endroits dans votre code. Par exemple, si vous définissez une variable avec le nom `XYZ` et que vous y accédez par la suite en utilisant le nom `xyz`, le compilateur considère les deux noms comme étant identiques.  
  
 En revanche, d’autres langages comme [C\#](../Topic/C%23.md) et [Visual C\+\+](../top/visual-cpp-in-visual-studio-2015.md) respectent la casse. Dans ces langages, `XYZ` et `xyz` sont considérés comme des noms différents. Par conséquent, une classe écrite dans ces langages peut définir une variable nommée `XYZ` et une propriété nommée `xyz`. Le Common Language Runtime \(CLR\) maintient le respect de la casse dans les assemblys. Toutefois, si une application Visual Basic accède à un assembly portant les noms `XYZ` et `xyz`, ceux\-ci apparaissent avec le même nom.  
  
 **ID d’erreur :** BC31429  
  
### Pour corriger cette erreur  
  
1.  Si vous contrôlez le code source du type de définition, pensez à renommer les membres pour qu’ils ne diffèrent pas uniquement par leur casse. Cela peut ne pas être possible si le type de définition a déjà été publié et qu’il est utilisé par d’autres applications.  
  
2.  Si vous ne pouvez pas renommer les membres dans le type de définition, supprimez l’élément de programmation cité de votre code. Vous ne pouvez pas accéder à un élément considéré comme ayant plusieurs définitions en Visual Basic.  
  
## Voir aussi  
 [Declared Element Names](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)   
 [Dépannage des variables](../Topic/Troubleshooting%20Variables%20in%20Visual%20Basic.md)   
 [Common Language Runtime](../Topic/Common%20Language%20Runtime%20\(CLR\).md)