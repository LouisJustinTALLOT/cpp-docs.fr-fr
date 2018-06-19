---
title: omp_get_wtime | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_wtime
dev_langs:
- C++
helpviewer_keywords:
- omp_get_wtime OpenMP function
ms.assetid: c8dee105-ec1b-42e5-a6e3-edeedcf9854c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ff7942a694bda3c28133aa0536fcacf9b341087
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690661"
---
# <a name="ompgetwtime"></a>omp_get_wtime
Retourne qu'une valeur en secondes du temps écoulé à partir d’un moment donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
double omp_get_wtime( );  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne qu'une valeur en secondes de la durée écoulée entre le moment de certaines arbitraire, mais il est cohérent.  
  
## <a name="remarks"></a>Notes  
 Ce point reste cohérent lors de l’exécution du programme, ce qui rend les comparaisons suivantes possible.  
  
 Pour plus d’informations, consultez [3.3.1 fonction omp_get_wtime](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md).  
  
## <a name="example"></a>Exemple  
  
```  
// omp_get_wtime.cpp  
// compile with: /openmp  
#include "omp.h"  
#include <stdio.h>  
#include <windows.h>  
  
int main() {  
    double start = omp_get_wtime( );  
    Sleep(1000);  
    double end = omp_get_wtime( );  
    double wtick = omp_get_wtick( );  
  
    printf_s("start = %.16g\nend = %.16g\ndiff = %.16g\n",  
             start, end, end - start);  
  
    printf_s("wtick = %.16g\n1/wtick = %.16g\n",  
             wtick, 1.0 / wtick);  
}  
```  
  
```Output  
start = 594255.3671159324  
end = 594256.3664474116  
diff = 0.9993314791936427  
wtick = 2.793651148400146e-007  
1/wtick = 3579545  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions](../../../parallel/openmp/reference/openmp-functions.md)