---
title: 3.2.5 Fonctions omp_test_lock and omp_test_nest_lock
ms.date: 11/04/2016
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
ms.openlocfilehash: e8e03699f807f23f139075560592d8846467f2c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512748"
---
# <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 Fonctions omp_test_lock and omp_test_nest_lock

Ces fonctions tentent de définition d’un verrou, mais ils ne bloquent pas l’exécution du thread. Le format est le suivant :

```
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

L’argument doit pointer vers une variable initialisée de verrou. Ces fonctions essayez de définir un verrou de la même manière que `omp_set_lock` et `omp_set_nest_lock`, sauf qu’ils ne bloquent pas l’exécution du thread.

Pour obtenir un verrou simple, le `omp_test_lock` fonction retourne une valeur différente de zéro si le verrou est défini correctement ; sinon, elle retourne zéro.

Pour obtenir un verrou pouvant être imbriqué, le `omp_test_nest_lock` fonction retourne le nouveau nombre d’imbrication si le verrou est défini correctement ; sinon, elle retourne zéro.