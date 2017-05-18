---
title: critiques | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Critical
dev_langs:
- C++
helpviewer_keywords:
- critical OpenMP directive
ms.assetid: 2ab87d6d-5ca4-43ae-9f0a-1f517a6a2bab
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 5693a16faebbc0f8c0a29cf28910110fbff66318
ms.contentlocale: fr-fr
ms.lasthandoff: 02/24/2017

---
# <a name="critical"></a>critical
Spécifie que code est uniquement exécutée sur un thread à la fois.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma omp critical [(name)]  
{  
   code_block  
}  
```  
  
## <a name="remarks"></a>Remarques  
 où,  
  
 (`name`) (facultatif)  
 Un nom pour identifier le code critique. Notez que ce nom doit être entre parenthèses.  
  
## <a name="remarks"></a>Remarques  
 Le **critique** directive prend en charge aucune clause OpenMP.  
  
 Pour plus d’informations, consultez [critique&2;.6.2 construction](../../../parallel/openmp/2-6-2-critical-construct.md).  
  
## <a name="example"></a>Exemple  
  
```  
// omp_critical.cpp  
// compile with: /openmp   
#include <omp.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
#define SIZE 10  
  
int main()   
{  
    int i;  
    int max;  
    int a[SIZE];  
  
    for (i = 0; i < SIZE; i++)   
    {  
        a[i] = rand();  
        printf_s("%d\n", a[i]);  
    }  
  
    max = a[0];  
    #pragma omp parallel for num_threads(4)  
        for (i = 1; i < SIZE; i++)   
        {  
            if (a[i] > max)  
            {  
                #pragma omp critical  
                {  
                    // compare a[i] and max again because max   
                    // could have been changed by another thread after   
                    // the comparison outside the critical section  
                    if (a[i] > max)  
                        max = a[i];  
                }  
            }  
        }  
  
    printf_s("max = %d\n", max);  
}  
```  
  
```Output  
41  
18467  
6334  
26500  
19169  
15724  
11478  
29358  
26962  
24464  
max = 29358  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)
