---
title: atomique | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- atomic
dev_langs:
- C++
helpviewer_keywords:
- atomic OpenMP directive
ms.assetid: 275e0338-cf2f-4525-97b5-696250000df7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf6287ff3c44d508a3e4293340e652edb201282f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694405"
---
# <a name="atomic"></a>atomique
Spécifie qu’un emplacement de mémoire qui sera mise à jour atomiquement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma omp atomic  
   expression  
```  
  
#### <a name="parameters"></a>Paramètres  
 `expression`  
 L’instruction contenant la valeur lvalue dont l’emplacement de mémoire que vous souhaitez protéger contre plusieurs écritures. Pour plus d’informations sur les formes expression juridique, consultez la spécification OpenMP.  
  
## <a name="remarks"></a>Notes  
 Le `atomic` directive prend en charge aucune clauses OpenMP.  
  
 Pour plus d’informations, consultez [2.6.4 atomique construire](../../../parallel/openmp/2-6-4-atomic-construct.md).  
  
## <a name="example"></a>Exemple  
  
```  
// omp_atomic.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
#define MAX 10  
  
int main() {  
   int count = 0;  
   #pragma omp parallel num_threads(MAX)  
   {  
      #pragma omp atomic  
      count++;  
   }  
   printf_s("Number of threads: %d\n", count);  
}  
```  
  
```Output  
Number of threads: 10  
```  
  
## <a name="see-also"></a>Voir aussi  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)