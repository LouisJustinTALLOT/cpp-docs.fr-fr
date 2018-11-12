---
title: A.8   Spécification des sections parallel
ms.date: 11/04/2016
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
ms.openlocfilehash: 81eaed920e77b23052ac58c2d0e18fee83c00565
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461436"
---
# <a name="a8---specifying-parallel-sections"></a>A.8   Spécification des sections parallel

Dans l’exemple suivant, (pour [Section 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) page 14) fonctions *xaxis*, *yaxis*, et *zaxis* peuvent être exécutées simultanément. Le premier `section` directive est facultative.  Notez que tous les `section` directives doivent apparaître dans l’étendue lexicale de la `parallel sections` construire.

```
#pragma omp parallel sections
{
    #pragma omp section
        xaxis();
    #pragma omp section
        yaxis();
    #pragma omp section
        zaxis();
}
```