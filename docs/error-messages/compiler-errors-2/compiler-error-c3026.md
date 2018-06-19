---
title: Erreur du compilateur C3026 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3026
dev_langs:
- C++
helpviewer_keywords:
- C3026
ms.assetid: 3297060e-cc5b-4600-a2db-09bfc4ffa21f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dede783f99015d464d31f2bc46cd548dd9a7b9b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243706"
---
# <a name="compiler-error-c3026"></a>Erreur du compilateur C3026
'clause' : l’expression constante doit être positive  
  
 Une valeur entière a été passée à une clause, mais il ne s’agissait pas d’un nombre positif. Le nombre doit être positif.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3026 :  
  
```  
// C3026.cpp  
// compile with: /openmp /link vcomps.lib  
#include <stdio.h>  
#include "omp.h"  
  
int main()  
{  
    int i;  
    const int i1 = 0;  
  
    #pragma omp parallel for num_threads(i1)   // C3026  
    for (i = 1; i <= 2; ++i)  
        printf_s("Hello World - thread %d - iteration %d\n",  
                 omp_get_thread_num(), i);  
  
    #pragma omp parallel for num_threads(i1 + 1)   // OK  
    for (i = 1; i <= 2; ++i)  
        printf_s("Hello World - thread %d - iteration %d\n",  
                 omp_get_thread_num(), i);  
}  
```