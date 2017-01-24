---
title: "La variable &#39;&lt;nom_variable&gt;&#39; est pass&#233;e par r&#233;f&#233;rence avant qu’une valeur lui ait &#233;t&#233; attribu&#233;e (variable de structure) | Microsoft Docs"
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
  - "bc42108"
  - "vbc42108"
helpviewer_keywords: 
  - "BC42108"
ms.assetid: 8f858dd7-db04-408e-ae67-e4ff2f0e5e30
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable &#39;&lt;nom_variable&gt;&#39; est pass&#233;e par r&#233;f&#233;rence avant qu’une valeur lui ait &#233;t&#233; attribu&#233;e (variable de structure)
La variable '\<nom\_variable\>' est passée par référence avant qu’une valeur lui ait été attribuée. Cela peut provoquer une exception de référence null au moment de l'exécution. Vérifiez que la structure et tous les membres de référence sont initialisés avant leur utilisation  
  
 Un appel de procédure passe une variable de structure en tant qu’argument à un paramètre `ByRef` avant l’assignation d’une valeur à la variable.  
  
 Si une valeur n’a jamais été assignée à une variable de structure, chaque membre de structure contient la valeur par défaut pour son type de données. Pour un type de données de référence, cette valeur par défaut est [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md). La lecture d’un membre de référence avec la valeur `Nothing` peut entraîner une exception <xref:System.NullReferenceException> dans certaines circonstances.  
  
 Quand un argument est passé à une procédure `ByRef`, cette dernière peut apporter des modifications à la variable sous\-jacente à l’argument.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **ID d’erreur :** BC42108  
  
### Pour corriger cette erreur  
  
-   Si vous souhaitez que la procédure affecte des valeurs aux membres de structure par le biais de l’argument `ByRef` et qu’il vous importe peu que les membres contiennent déjà des valeurs, aucune action n’est nécessaire.  
  
-   Si la logique de la procédure lit un membre de structure avant de lui assigner une valeur et que le membre est un type valeur, vérifiez que la logique de la procédure ne dépend pas de la présence ou non dans le membre de sa valeur par défaut.  
  
-   Si la logique de la procédure lit un membre de structure avant de lui assigner une valeur et que le membre est un type référence, vérifiez que la logique de la procédure peut gérer une valeur `Nothing`. Par exemple, elle peut utiliser [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md) pour intercepter <xref:System.NullReferenceException>.  
  
## Voir aussi  
 [Dim Statement](../Topic/Dim%20Statement%20\(Visual%20Basic\).md)   
 [Value Types and Reference Types](../Topic/Value%20Types%20and%20Reference%20Types.md)   
 [Passing Arguments by Value and by Reference](../Topic/Passing%20Arguments%20by%20Value%20and%20by%20Reference%20\(Visual%20Basic\).md)   
 [ByRef](../Topic/ByRef%20\(Visual%20Basic\).md)   
 [Déclaration de variable](../Topic/Variable%20Declaration%20in%20Visual%20Basic.md)   
 [Structures](../Topic/Structures%20\(Visual%20Basic\).md)   
 [Structure Statement](../Topic/Structure%20Statement.md)   
 [Dépannage des variables](../Topic/Troubleshooting%20Variables%20in%20Visual%20Basic.md)