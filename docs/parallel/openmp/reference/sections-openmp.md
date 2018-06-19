---
title: sections (OpenMP) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- section
- SECTIONS
dev_langs:
- C++
helpviewer_keywords:
- sections OpenMP directive
ms.assetid: 4cd1d776-e198-470e-930a-01fb0ab0a0bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60bc94685a7e6128e22cc3545ae8702abe6d472e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692075"
---
# <a name="sections-openmp"></a>sections (OpenMP)
Identifie les sections de code pour être réparti entre tous les threads.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma omp [parallel] sections [clauses]  
{  
   #pragma omp section  
   {  
      code_block   
   }   
}  
```  
  
## <a name="remarks"></a>Notes  
 où,  
  
 `clause`(facultatif)  
 Zéro ou plusieurs clauses. Consultez la section Notes pour obtenir la liste des clauses prises en charge par **sections**.  
  
## <a name="remarks"></a>Notes  
 Le **sections** directive peut contenir zéro ou plusieurs **section** directives.  
  
 Le **sections** directive prend en charge les clauses OpenMP suivantes :  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [lastprivate](../../../parallel/openmp/reference/lastprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
 Si **parallèles** est également spécifiée, `clause` peut être n’importe quelle clause acceptée par le **parallèles** ou **sections** directives, à l’exception de `nowait`.  
  
 Pour plus d’informations, consultez [2.4.2 construction sections](../../../parallel/openmp/2-4-2-sections-construct.md).  
  
## <a name="example"></a>Exemple  
  
```  
// omp_sections.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
    #pragma omp parallel sections num_threads(4)  
    {  
        printf_s("Hello from thread %d\n", omp_get_thread_num());  
        #pragma omp section  
        printf_s("Hello from thread %d\n", omp_get_thread_num());  
    }  
}  
```  
  
```Output  
Hello from thread 0  
Hello from thread 0  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)