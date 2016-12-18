---
title: "La classe &#39;&lt;nom_classe&gt;&#39; doit &#234;tre d&#233;clar&#233;e &#39;MustInherit&#39; ou se substituer aux membres &#39;MustOverride&#39; h&#233;rit&#233;s suivants&#160;: &lt;noms_membres&gt;. | Microsoft Docs"
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
  - "bc30610"
  - "vbc30610"
helpviewer_keywords: 
  - "BC30610"
ms.assetid: 7fba7a3b-c918-44ba-ae85-20312615c1ce
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La classe &#39;&lt;nom_classe&gt;&#39; doit &#234;tre d&#233;clar&#233;e &#39;MustInherit&#39; ou se substituer aux membres &#39;MustOverride&#39; h&#233;rit&#233;s suivants&#160;: &lt;noms_membres&gt;.
Les classes dérivées de classes de base qui contiennent des membres `MustOverride` doivent remplacer ces membres ou utiliser le modificateur `MustInherit`.  
  
 **ID d’erreur :** BC30610  
  
### Pour corriger cette erreur  
  
-   Ajoutez le modificateur `MustInherit` à la définition de classe.  
  
-   Déclarez une substitution à l’aide du mot clé `Overrides`.  
  
## Voir aussi  
 [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)   
 [MustInherit](../Topic/MustInherit%20\(Visual%20Basic\).md)   
 [NOT IN BUILD : Héritage en Visual Basic](http://msdn.microsoft.com/fr-fr/e5e6e240-ed31-4657-820c-079b7c79313c)