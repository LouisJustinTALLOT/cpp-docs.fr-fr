---
title: omp_set_num_threads | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_num_threads
dev_langs:
- C++
helpviewer_keywords:
- omp_set_num_threads OpenMP function
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 335cb283026a019d6c6a03565c5dbec541140db3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691311"
---
# <a name="ompsetnumthreads"></a>omp_set_num_threads
Définit le nombre de threads dans les régions parallèles suivantes, sauf si un [num_threads](../../../parallel/openmp/reference/num-threads.md) clause.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void omp_set_num_threads(  
   int num_threads  
);  
```  
  
## <a name="remarks"></a>Notes  
 où,  
  
 `num_threads`  
 Le nombre de threads dans la région parallèle.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [3.1.1 fonction omp_set_num_threads](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).  
  
## <a name="example"></a>Exemple  
 Consultez [omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md) pour obtenir un exemple d’utilisation de `omp_set_num_threads`.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions](../../../parallel/openmp/reference/openmp-functions.md)