---
title: A.3   Utilisation des régions parallèles
ms.date: 11/04/2016
ms.assetid: 575216a1-960a-47f7-9c82-7f660291fcfe
ms.openlocfilehash: 573c4f7c47c90bc6d567c4640360aa6abee5a48c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458992"
---
# <a name="a3---using-parallel-regions"></a>A.3   Utilisation des régions parallèles

Le `parallel` directive ([Section 2.3](../../parallel/openmp/2-3-parallel-construct.md) page 8) peut être utilisé dans les programmes parallèles de granularité grossière. Dans l’exemple suivant, chaque thread dans la région parallèle décide quelle partie du tableau global `x` travailler, en fonction du nombre de threads :

```
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)
{
    iam = omp_get_thread_num();
    np =  omp_get_num_threads();
    ipoints = npoints / np;
    subdomain(x, iam, ipoints);
}
```