---
title: "Erreur du compilateur C3054 | Microsoft Docs"
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
  - "C3054"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3054"
ms.assetid: 6f4b7ac5-0d12-474b-b611-76ff26ee41ac
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Erreur du compilateur C3054
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\#pragma omp parallel' n'est pas pris en charge actuellement dans une classe ou fonction générique  
  
 Pour plus d’informations, consultez [Generics](../../windows/generics-cpp-component-extensions.md) et [OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md).  
  
## Exemple  
 L’exemple suivant génère l’erreur C3054.  
  
```  
// C3054.cpp // compile with: /openmp /clr /c #include <omp.h> ref struct MyBaseClass { // Delete the following 7 lines to resolve. generic <class ItemType> void Test(ItemType i) {   // C3054 #pragma omp parallel num_threads(4) { int i = omp_get_thread_num(); } } // OK void Test2() { #pragma omp parallel num_threads(4) { int i = omp_get_thread_num(); } } };  
```