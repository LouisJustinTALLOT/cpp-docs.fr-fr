---
title: "Impossible d’utiliser le caract&#232;re &#39;?&#39; ici | Microsoft Docs"
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
  - "bc36637"
  - "vbc36637"
helpviewer_keywords: 
  - "BC36637"
ms.assetid: a54c46e7-8fd8-4941-9fce-72f2b41b5e24
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’utiliser le caract&#232;re &#39;?&#39; ici
Le caractère « ? » peut être utilisé pour spécifier qu’un type valeur ou une structure est Nullable. Son utilisation dans d’autres circonstances est limitée. Par exemple, le code suivant génère cette exception.  
  
```  
' Not valid. ' #Const found = True?  
```  
  
 **ID d’erreur :** BC36637  
  
### Pour corriger cette erreur  
  
-   Supprimez le caractère « ? » de la déclaration.  
  
## Voir aussi  
 [Nullable Value Types](../Topic/Nullable%20Value%20Types%20\(Visual%20Basic\).md)