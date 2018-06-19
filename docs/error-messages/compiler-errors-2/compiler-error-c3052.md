---
title: Erreur du compilateur C3052 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3052
dev_langs:
- C++
helpviewer_keywords:
- C3052
ms.assetid: 87480c42-1ceb-4775-8d20-88c54a7bb6a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96db942b0ed50114378843b9f88fd77b2d24d771
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244196"
---
# <a name="compiler-error-c3052"></a>Erreur du compilateur C3052
'var' : la variable n’apparaît pas dans une clause de partage de données sous une clause default(none)  
  
 Si [default(none)](../../parallel/openmp/reference/default-openmp.md) est utilisé, toute variable utilisée dans le bloc structuré doit être spécifiée explicitement comme [shared](../../parallel/openmp/reference/shared-openmp.md) ou [private](../../parallel/openmp/reference/private-openmp.md).  
  
 L’exemple suivant génère l’erreur C3052 :  
  
```  
// C3052.cpp  
// compile with: /openmp /c  
int main() {  
   int n1 = 1;  
  
   #pragma omp parallel default(none) // shared(n1) private(n1)  
   {  
      n1 = 0;   // C3052 use either a shared or private clause  
   }  
}  
```