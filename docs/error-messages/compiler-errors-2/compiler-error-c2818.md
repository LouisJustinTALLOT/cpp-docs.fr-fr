---
title: "Erreur du compilateur C2818 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2818"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2818"
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Erreur du compilateur C2818
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

L'application de l' 'opérateur \-\>' surchargé est récurrente à travers le type 'type'  
  
 Une redéfinition de l'opérateur d'accès au membre de classe contient une instruction `return` récurrente.  Pour redéfinir l'opérateur `->` avec récurrence, vous devez déplacer la routine récurrente vers une fonction appelée à partir de la fonction de substitution de l'opérateur.