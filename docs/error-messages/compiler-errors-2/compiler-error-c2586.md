---
title: "Erreur du compilateur C2586 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2586"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2586"
ms.assetid: dae703c7-5c38-4db6-8411-4d1b22713eb5
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Erreur du compilateur C2586
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

syntaxe de la conversion définie par l'utilisateur incorrecte : indirections non conformes  
  
 L'indirection d'un opérateur de conversion n'est pas autorisée.  
  
 L'exemple suivant génère l'erreur C2586 :  
  
```  
// c2586.cpp  
// compile with: /c  
struct C {  
   * operator int();   // C2586  
   operator char();   // OK  
};  
```