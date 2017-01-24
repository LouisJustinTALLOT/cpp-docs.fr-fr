---
title: "Erreur du compilateur C2191 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2191"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2191"
ms.assetid: 051b8350-e5de-4f51-ab6e-96d32366bcef
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Erreur du compilateur C2191
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

seconde liste de paramètres plus longue que la première  
  
 Une fonction C a été déclarée une seconde fois avec une liste de paramètres plus longue.  C ne prend pas en charge les fonctions surchargées.  
  
## Exemple  
 L'exemple suivant génère l'erreur C2191 :  
  
```  
// C2191.c  
// compile with: /Za /c  
void func( int );  
void func( int, float );   // C2191 different parameter list  
void func2( int, float );   // OK  
```