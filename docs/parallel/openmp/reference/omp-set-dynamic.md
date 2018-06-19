---
title: omp_set_dynamic | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_set_dynamic OpenMP function
ms.assetid: 3845faf2-a0ca-45a5-ae70-2a7a6164f1e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18521113125eb49fa413568b6a62472bb50a7924
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691948"
---
# <a name="ompsetdynamic"></a>omp_set_dynamic
Indique que le nombre de threads disponibles dans une région parallèle suivante peut être ajusté par le temps d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_set_dynamic(  
   int val  
);  
```  
  
## <a name="remarks"></a>Notes  
 où,  
  
 `val`  
 Une valeur qui indique si le nombre de threads disponibles dans une région parallèle suivante peut être ajustée par le runtime.  Si elle est différente de zéro, que le runtime peut ajuster le nombre de threads, si zéro, le runtime s’ajustent pas dynamiquement le nombre de threads.  
  
## <a name="remarks"></a>Notes  
 Le nombre de threads ne dépassera jamais la valeur définie par [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) ou par [OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md).  
  
 Utilisez [omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md) pour afficher le paramètre actuel de `omp_set_dynamic`.  
  
 Le paramètre de `omp_set_dynamic` remplace le paramètre de la [OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md) variable d’environnement.  
  
 Pour plus d’informations, consultez [3.1.7 fonction omp_set_dynamic](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).  
  
## <a name="example"></a>Exemple  
  
```  
// omp_set_dynamic.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main()   
{  
    omp_set_dynamic(9);  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_dynamic( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_dynamic( ));  
        }  
}  
```  
  
```Output  
1  
1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions](../../../parallel/openmp/reference/openmp-functions.md)