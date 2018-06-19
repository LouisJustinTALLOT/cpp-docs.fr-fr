---
title: 3.1.4 fonction omp_get_thread_num | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fad749b91470f7834169fe8ed734f1d627aa228e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686069"
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 Fonction omp_get_thread_num
Le `omp_get_thread_num` fonction retourne le nombre de threads, au sein de son équipe, du thread d’exécution de la fonction. Le se trouve de thread nombre compris entre 0 et **omp_get_num_threads()**-1, inclus. Le thread principal de l’équipe est 0.  
  
 Le format est le suivant :  
  
```  
#include <omp.h>  
int omp_get_thread_num(void);  
```  
  
 Si elle est appelée à partir d’une région de série, `omp_get_thread_num` retourne 0. Si l’appelé à partir d’une région parallèle imbriquée qui est sérialisée, cette fonction retourne 0.  
  
## <a name="cross-references"></a>Références externes :  
  
-   `omp_get_num_threads` fonction, consultez [Section 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) à la page 37.