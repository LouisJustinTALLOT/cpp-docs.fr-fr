---
title: A.5   Utilisation de la directive critical
ms.date: 11/04/2016
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
ms.openlocfilehash: 82497d63acc057fbbcf26f585e42fc8611c08ec4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545096"
---
# <a name="a5---using-the-critical-directive"></a>A.5   Utilisation de la directive critical

L’exemple suivant inclut plusieurs `critical` directives ([Section 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) à la page 18). L’exemple illustre un modèle de file d’attente dans laquelle une tâche est dépilée et a travaillé sur. Pour vous protéger contre plusieurs threads du retrait de la même tâche, l’opération de retrait doit être dans un `critical` section. Étant donné que les deux files d’attente dans cet exemple sont indépendants, ils sont protégés par `critical` directives avec des noms différents, *xaxis* et *yaxis*.

```
#pragma omp parallel shared(x, y) private(x_next, y_next)
{
    #pragma omp critical ( xaxis )
        x_next = dequeue(x);
    work(x_next);
    #pragma omp critical ( yaxis )
        y_next = dequeue(y);
    work(y_next);
}
```