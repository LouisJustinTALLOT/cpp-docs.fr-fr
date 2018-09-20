---
title: A.18 Directives for imbriquées | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ae2b2e0b-ec94-43f8-928c-6d621b51f0df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a4e8a984a111d409e07d55c0c1f6e6adbed91e4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433567"
---
# <a name="a18---nested-for-directives"></a>A.18   Directives for imbriquées

L’exemple suivant de `for` imbrication de directives ([Section 2.9](../../parallel/openmp/2-9-directive-nesting.md) sur la page 33) est conforme, car intérieurs et extérieurs `for` directives lier à différentes régions parallèles :

```
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
        {
            #pragma omp parallel shared(i, n)
            {
                #pragma omp for
                    for (j=0; j<n; j++)
                        work(i, j);
            }
        }
}
```

Une variante suivante de l’exemple précédent est également conforme :

```
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
            work1(i, n);
}

void work1(int i, int n)
{
    int j;
    #pragma omp parallel default(shared)
    {
        #pragma omp for
            for (j=0; j<n; j++)
                work2(i, j);
    }
    return;
}
```