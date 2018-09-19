---
title: atomique | Microsoft Docs
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
ms.openlocfilehash: e7e9e9ecad2f6ea53e2f922799340eee47dd4a7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037487"
---
# <a name="atomic"></a>atomique
Spécifie qu’un emplacement de mémoire qui sera mis à jour atomiquement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma omp atomic  
   expression  
```  
  
#### <a name="parameters"></a>Paramètres  
*Expression*<br/>
L’instruction contenant la valeur lvalue dont l’emplacement de mémoire que vous souhaitez protéger contre plusieurs écritures. Pour plus d’informations sur les formulaires de l’expression juridiques, consultez la spécification OpenMP.  
  
## <a name="remarks"></a>Notes  
 Le `atomic` directive prend en charge aucune clause OpenMP.  
  
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