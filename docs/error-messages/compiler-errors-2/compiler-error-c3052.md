---
title: "Erreur du compilateur C3052 | Microsoft Docs"
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
  - "C3052"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3052"
ms.assetid: 87480c42-1ceb-4775-8d20-88c54a7bb6a6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Erreur du compilateur C3052
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' : la variable n’apparaît pas dans une clause de partage de données sous une clause default\(none\)  
  
 Si [default\(none\)](../../parallel/openmp/reference/default-openmp.md) est utilisé, toute variable utilisée dans le bloc structuré doit être spécifiée explicitement comme [shared](../../parallel/openmp/reference/shared-openmp.md) ou [private](../../parallel/openmp/reference/private-openmp.md).  
  
 L’exemple suivant génère l’erreur C3052 :  
  
```  
// C3052.cpp // compile with: /openmp /c int main() { int n1 = 1; #pragma omp parallel default(none) // shared(n1) private(n1) { n1 = 0;   // C3052 use either a shared or private clause } }  
```