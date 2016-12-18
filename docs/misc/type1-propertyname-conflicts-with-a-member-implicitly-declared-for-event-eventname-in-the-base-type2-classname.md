---
title: "&lt;type1&gt; &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; est en conflit avec un membre implicitement d&#233;clar&#233; pour &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; dans le &lt;type2&gt; &#39;&lt;nom_classe&gt;&#39; de base | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40014"
  - "bc40014"
helpviewer_keywords: 
  - "BC40014"
ms.assetid: 100534b9-d533-4e94-a2a7-0ed26426965b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt; &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; est en conflit avec un membre implicitement d&#233;clar&#233; pour &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; dans le &lt;type2&gt; &#39;&lt;nom_classe&gt;&#39; de base
Une propriété est déclarée avec le même nom qu’un membre implicite formé à partir d’un événement dans la classe de base. Par exemple, si la classe de base définit un événement nommé `Event1`, le compilateur génère les procédures implicites `add_Event1` et `remove_Event1`. Si la propriété dans cette classe a l’un de ces noms, elle doit occulter le membre de classe de base.  
  
 Ce message est un avertissement.`Shadows` est supposé par défaut. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **ID d’erreur :** BC40014  
  
### Pour corriger cette erreur  
  
1.  Pour masquer le membre de classe de base, ajoutez le mot clé `Shadows` à la déclaration de propriété.  
  
2.  Si vous ne prévoyez pas de masquer le membre de classe de base, changez le nom de la propriété.  
  
## Voir aussi  
 [Property Statement](../Topic/Property%20Statement.md)   
 [Event Statement](../Topic/Event%20Statement.md)   
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)   
 [Shadowing in Visual Basic](../Topic/Shadowing%20in%20Visual%20Basic.md)