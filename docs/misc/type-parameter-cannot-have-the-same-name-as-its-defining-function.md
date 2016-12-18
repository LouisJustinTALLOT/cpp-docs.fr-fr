---
title: "Un param&#232;tre de type ne peut pas avoir le m&#234;me nom que sa fonction de d&#233;finition | Microsoft Docs"
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
  - "vbc32090"
  - "bc32090"
helpviewer_keywords: 
  - "BC32090"
ms.assetid: 02f4d82c-dcd7-44cc-b725-81e235f680f6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Un param&#232;tre de type ne peut pas avoir le m&#234;me nom que sa fonction de d&#233;finition
Un paramètre de type d’un type générique est déclaré avec le même nom que le type générique.  
  
 Dans la liste des paramètres de type d’un type générique, chaque paramètre de type doit avoir un nom différent de tous les noms suivants :  
  
-   tout autre paramètre de type présent dans la même liste de paramètres de type ;  
  
-   chaque paramètre de type présent dans la liste des paramètres de type d’un type générique conteneur ; et  
  
-   le nom du type générique lui\-même.  
  
 **ID d’erreur :** BC32090  
  
### Pour corriger cette erreur  
  
-   Renommez le paramètre de type à distinguer de chaque nom cité dans la liste de cette page d’aide.  
  
## Voir aussi  
 [Types génériques Visual Basic](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)   
 [Type List](../Topic/Type%20List%20\(Visual%20Basic\).md)