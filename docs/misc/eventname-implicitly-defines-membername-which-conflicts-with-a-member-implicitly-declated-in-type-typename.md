---
title: "&#39;&lt;nom_&#233;v&#233;nement&gt;&#39; d&#233;finit implicitement &#39;&lt;nom_membre&gt;&#39;, qui est en conflit avec un membre d&#233;clar&#233; implicitement dans le &lt;type&gt; &#39;&lt;nom_type&gt;&#39; | Microsoft Docs"
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
  - "bc31059"
  - "vbc31059"
helpviewer_keywords: 
  - "BC31059"
ms.assetid: 60ddb2f4-a204-41eb-b13b-b2bb13ddb69c
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; d&#233;finit implicitement &#39;&lt;nom_membre&gt;&#39;, qui est en conflit avec un membre d&#233;clar&#233; implicitement dans le &lt;type&gt; &#39;&lt;nom_type&gt;&#39;
Le nom d’un membre de type est en conflit avec le nom d’un membre créé implicitement pour un événement. Les événements créent implicitement plusieurs variables. Par exemple, la déclaration `Event X` déclare implicitement les noms `XEventHandler`, `XEvent`, `add_X` et `remove_X`.  
  
 **ID d’erreur :** BC31059  
  
### Pour corriger cette erreur  
  
-   Renommez le membre déclaré explicitement pour supprimer le conflit de noms.  
  
## Voir aussi  
 [NotInBuild : Instructions de déclaration en Visual Basic](http://msdn.microsoft.com/fr-fr/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)