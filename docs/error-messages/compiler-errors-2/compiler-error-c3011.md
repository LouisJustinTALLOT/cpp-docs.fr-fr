---
title: "Erreur du compilateur C3011 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3011"
ms.assetid: 24c3a917-ebff-4deb-9155-23adf6468531
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Erreur du compilateur C3011
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

assembly inline non autorisé directement dans une région parallèle  
  
 Une région parallèle `omp` ne peut pas contenir d’instructions d’assembly inline.  
  
 L’exemple suivant génère l’erreur C3011 :  
  
```  
// C3011.cpp // compile with: /openmp // processor: /x86 int main() { int   n = 0; #pragma omp parallel { _asm mov eax, n   // Delete this line to resolve this error. }   // C3011 }  
```