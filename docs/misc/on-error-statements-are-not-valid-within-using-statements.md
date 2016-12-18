---
title: "Les instructions &#39;On Error&#39; ne sont pas valides dans les instructions &#39;Using&#39; | Microsoft Docs"
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
  - "vbc36013"
  - "bc36013"
helpviewer_keywords: 
  - "BC36013"
ms.assetid: 5b399bf9-6595-46e0-a808-378f6c28568b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les instructions &#39;On Error&#39; ne sont pas valides dans les instructions &#39;Using&#39;
Une instruction `On Error` apparaît dans une instruction `Using`, mais n’est pas valide dans ce contexte.  
  
 **ID d’erreur :** BC36013  
  
### Pour corriger cette erreur  
  
-   Utilisez une gestion structurée des erreurs, par exemple un bloc `Try…Catch`, au lieu de l’instruction `On Error`.  
  
## Voir aussi  
 [Vue d’ensemble de la gestion structurée des exceptions pour Visual Basic](http://msdn.microsoft.com/fr-fr/bb81af80-a735-4873-9711-6151a48e418a)   
 [Cas d’utilisation de la gestion structurée ou non structurée des exceptions \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/e897d7ca-07e8-45dd-8a6d-a5b2a2fc9b9a)   
 [On Error Statement](../Topic/On%20Error%20Statement%20\(Visual%20Basic\).md)   
 [Comment : tester du code à l’aide d’un bloc Try...Catch dans Visual Basic](http://msdn.microsoft.com/fr-fr/8368e205-ed73-4185-a247-af84fb4fafa9)   
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)