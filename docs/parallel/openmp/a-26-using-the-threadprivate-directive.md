---
title: A.26   Utilisation de la directive threadprivate
ms.date: 11/04/2016
ms.assetid: 6eda76c2-c4f1-4208-a900-e0ea98a53eca
ms.openlocfilehash: 8ea810f8fbf8076b28464faafb72f5797d4a1a66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465427"
---
# <a name="a26---using-the-threadprivate-directive"></a>A.26   Utilisation de la directive threadprivate

Les exemples suivants montrent comment utiliser le `threadprivate` directive ([Section 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) à la page 23) afin de donner à chaque thread un compteur distinct.

**Exemple 1 :**

```
int counter = 0;
#pragma omp threadprivate(counter)

int sub()
{
    counter++;
    return(counter);
}
```

**Exemple 2 :**

```
int sub()
{
    static int counter = 0;
    #pragma omp threadprivate(counter)
    counter++;
    return(counter);
}
```