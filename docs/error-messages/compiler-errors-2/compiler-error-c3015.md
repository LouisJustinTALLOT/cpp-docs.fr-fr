---
title: "Erreur du compilateur C3015 | Microsoft Docs"
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
  - "C3015"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3015"
ms.assetid: d5e8e50b-7542-4b2d-8665-1b22072a5bc6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Erreur du compilateur C3015
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

forme incorrecte de l'initialisation dans l'instruction 'for' OpenMP  
  
 Une boucle `for` dans une instruction OpenMP doit être spécifiée complètement et explicitement.  
  
 L’exemple suivant génère l’erreur C3015 :  
  
```  
// C3015.cpp // compile with: /openmp int main() { int i = 0, j = 10; #pragma omp parallel { #pragma omp for for (; i < 0; i += j)   // C3015 // Try the following line instead: // for (i = 0; i < 0; i++) --j; } }  
```