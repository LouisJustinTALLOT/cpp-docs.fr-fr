---
title: A.1   Exécution d'une boucle simple en parallèle
ms.date: 11/04/2016
ms.assetid: b8aaacae-b20d-4b16-a540-54ccbf09582b
ms.openlocfilehash: 5bd9a9c8b1d226c67f7e9031a547e551fae3407b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558936"
---
# <a name="a1---executing-a-simple-loop-in-parallel"></a>A.1   Exécution d'une boucle simple en parallèle

L’exemple suivant montre comment paralléliser une boucle simple à l’aide de la `parallel for` directive ([Section 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) page 16). La variable d’itération de boucle est privée par défaut, il est donc pas nécessaire de spécifier explicitement dans une clause privée.

```
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```