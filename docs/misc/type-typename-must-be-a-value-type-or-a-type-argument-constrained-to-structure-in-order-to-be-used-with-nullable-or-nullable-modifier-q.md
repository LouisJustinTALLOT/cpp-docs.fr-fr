---
title: "Le type &#39;&lt;nom_type&gt;&#39; doit &#234;tre un type valeur ou un argument de type limit&#233; &#224; &#39;Structure&#39; pour pouvoir &#234;tre utilis&#233; avec &#39;Nullable&#39; ou le modificateur autorisant les valeurs Null &#39;?&#39; | Microsoft Docs"
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
  - "vbc33101"
  - "bc33101"
helpviewer_keywords: 
  - "BC33101"
ms.assetid: b3e0e4e4-87b8-4a38-a450-15233497acaa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type &#39;&lt;nom_type&gt;&#39; doit &#234;tre un type valeur ou un argument de type limit&#233; &#224; &#39;Structure&#39; pour pouvoir &#234;tre utilis&#233; avec &#39;Nullable&#39; ou le modificateur autorisant les valeurs Null &#39;?&#39;
Seuls les types valeur, y compris les structures, peuvent être déclarés nullables.  
  
```vb#  
' Valid. Dim n? As Integer Dim m As Integer? ' Not valid. ' Dim p? As Object ' Dim q As Nullable(Of Object)  
```  
  
 **ID d’erreur :** BC33101  
  
### Pour corriger cette erreur  
  
-   Supprimez '?' ou `Nullable`.  
  
-   Utilisez un type de données valeur.  
  
## Voir aussi  
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)