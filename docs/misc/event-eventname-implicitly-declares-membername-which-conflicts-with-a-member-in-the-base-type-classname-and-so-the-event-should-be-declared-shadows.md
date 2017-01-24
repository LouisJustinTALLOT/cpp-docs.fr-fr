---
title: "L’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; d&#233;clare implicitement &#39;&lt;nom_membre&#39;, qui est en conflit avec un membre dans le &lt;type&gt; &#39;&lt;nom_classe&gt;&#39; de base. L’&#233;v&#233;nement doit &#234;tre d&#233;clar&#233; &#39;Shadows&#39; | Microsoft Docs"
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
  - "bc40012"
  - "vbc40012"
helpviewer_keywords: 
  - "BC40012"
ms.assetid: 5f14e8bd-a227-4115-af99-cd2b6fe4dc0e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; d&#233;clare implicitement &#39;&lt;nom_membre&#39;, qui est en conflit avec un membre dans le &lt;type&gt; &#39;&lt;nom_classe&gt;&#39; de base. L’&#233;v&#233;nement doit &#234;tre d&#233;clar&#233; &#39;Shadows&#39;
Un événement est déclaré avec un nom qui forme un membre implicite portant le même nom qu’un membre de la classe de base. Par exemple, si vous déclarez un événement nommé `Event1`, le compilateur génère les procédures implicites `add_Event1` et `remove_Event1`. Si la classe de base a un membre avec l’un de ces noms, l’événement de cette classe doit occulter le membre de classe de base.  
  
 Ce message est un avertissement.`Shadows` est supposé par défaut. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **ID d’erreur :** BC40012  
  
### Pour corriger cette erreur  
  
1.  Pour masquer le membre de classe de base, ajoutez le mot clé `Shadows` à la déclaration d’événement.  
  
2.  Si vous ne voulez pas masquer le membre de classe de base, changez le nom de l’événement.  
  
## Voir aussi  
 [Event Statement](../Topic/Event%20Statement.md)   
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)   
 [Shadowing in Visual Basic](../Topic/Shadowing%20in%20Visual%20Basic.md)