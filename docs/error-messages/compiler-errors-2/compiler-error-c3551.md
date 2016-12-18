---
title: "Erreur du compilateur C3551 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3551"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3551"
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Erreur du compilateur C3551
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

« type de retour spécifié à la fin attendu »  
  
 Si vous utilisez le mot clé `auto` en tant qu’espace réservé pour le type de retour d’une fonction, vous devez fournir un type de retour spécifié à la fin. Dans l’exemple suivant, le type de retour spécifié à la fin de la fonction `myFunction` est un pointeur vers un tableau de quatre éléments de type `int`.  
  
```  
auto myFunction()->int(*)[4];   
```  
  
## Voir aussi  
 [auto](../../cpp/auto-cpp.md)