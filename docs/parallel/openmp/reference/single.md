---
title: unique | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- Single
dev_langs:
- C++
helpviewer_keywords:
- single OpenMP directive
ms.assetid: 85cf94fb-cb9c-4d82-8609-adffa9f552e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ff1a255933b79d39b6eedbb9362ff76a34e0f8a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716987"
---
# <a name="single"></a>unique
Vous permet de spécifier qu’une section de code doit être exécutée sur un seul thread, mais pas nécessairement le thread principal.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma omp single [clauses]   
{  
   code_block   
}  
```  
  
#### <a name="parameters"></a>Paramètres  

`clause`  
(Facultatif) Zéro ou plusieurs clauses. Consultez la section Notes pour obtenir la liste des clauses prises en charge par **unique**.  
  
## <a name="remarks"></a>Notes  
 Le **unique** directive prend en charge les clauses OpenMP suivantes :  
  
-   [copyprivate](../../../parallel/openmp/reference/copyprivate.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
 Le [master](../../../parallel/openmp/reference/master.md) directive vous permet de spécifier qu’une section de code doit être exécutée uniquement sur le thread principal.  
  
 Pour plus d’informations, consultez [2.4.3 unique construire](../../../parallel/openmp/2-4-3-single-construct.md).  
  
## <a name="example"></a>Exemple  
  
```  
// omp_single.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
   #pragma omp parallel num_threads(2)  
   {  
      #pragma omp single  
      // Only a single thread can read the input.  
      printf_s("read input\n");  
  
      // Multiple threads in the team compute the results.  
      printf_s("compute results\n");  
  
      #pragma omp single  
      // Only a single thread can write the output.  
      printf_s("write output\n");  
    }  
}  
```  
  
```Output  
read input  
compute results  
compute results  
write output  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)