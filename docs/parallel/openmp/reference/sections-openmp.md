---
title: sections (OpenMP) | Microsoft Docs
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
ms.openlocfilehash: d3b369cfbd68edd32b644c9a4ec0520329507b6e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708030"
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
  
## <a name="arguments"></a>Arguments

*Clause*<br/>
(Facultatif) Zéro ou plusieurs clauses. Consultez la section Notes pour obtenir la liste des clauses prises en charge par **sections**.

## <a name="remarks"></a>Notes  
 Le **sections** directive peut contenir zéro ou plusieurs **section** directives.  
  
 Le **sections** directive prend en charge les clauses OpenMP suivantes :  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [lastprivate](../../../parallel/openmp/reference/lastprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
 Si **parallèles** est également spécifié, `clause` peut être toute clause acceptée par le **parallèles** ou **sections** directives, à l’exception `nowait`.  
  
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