---
title: A.12   Utilisation de la directive atomic
ms.date: 11/04/2016
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
ms.openlocfilehash: 0f75b182e2cae11f0e72d5ca1e67f887294e8f69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504433"
---
# <a name="a12---using-the-atomic-directive"></a>A.12   Utilisation de la directive atomic

L’exemple suivant permet d’éviter des conditions de concurrence (mises à jour simultanées d’un élément de *x* par plusieurs threads) à l’aide de la `atomic` directive ([Section 2.6.4](../../parallel/openmp/2-6-4-atomic-construct.md) à la page 19) :

```
#pragma omp parallel for shared(x, y, index, n)
    for (i=0; i<n; i++)
    {
        #pragma omp atomic
            x[index[i]] += work1(i);
        y[i] += work2(i);
    }
```

L’avantage d’utiliser le `atomic` directive dans cet exemple est qu’elle autorise les mises à jour de deux éléments différents de x être exécutées en parallèle. Si un `critical` directive ([Section 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) à la page 18) ont été utilisés à la place, puis toutes les mises à jour aux éléments de *x* serait exécuté en série (bien que non dans des garanties ordre).

Notez que la `atomic` directive s’applique uniquement à l’instruction C ou C++, il suit immédiatement.  Par conséquent, les éléments de *y* ne sont pas mises à jour de manière atomique dans cet exemple.