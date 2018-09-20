---
title: 3.1.4 fonction omp_get_thread_num | Microsoft Docs
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
ms.openlocfilehash: 5a21a682c051daffde16b3d5cfc63fd2d679c4de
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444916"
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 Fonction omp_get_thread_num

Le `omp_get_thread_num` fonction retourne le nombre de threads au sein de son équipe, du thread exécutant la fonction. Le se trouve de thread nombre compris entre 0 et **omp_get_num_threads()**-1, inclus. Le thread principal de l’équipe est 0.

Le format est le suivant :

```
#include <omp.h>
int omp_get_thread_num(void);
```

Si elle est appelée à partir d’une région de série, `omp_get_thread_num` retourne 0. Si elle est appelée à partir de dans une région parallèle imbriquée qui est sérialisée, cette fonction retourne 0.

## <a name="cross-references"></a>Références externes :

- `omp_get_num_threads` fonction, consultez [Section 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) sur la page 37.