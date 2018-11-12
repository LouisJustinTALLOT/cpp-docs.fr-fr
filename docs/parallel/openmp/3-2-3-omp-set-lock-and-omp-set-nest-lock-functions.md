---
title: 3.2.3 Fonctions omp_set_lock and omp_set_nest_lock
ms.date: 11/04/2016
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
ms.openlocfilehash: 8efc1f844be2d1b8cf9b15242758914edd0fca14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617657"
---
# <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 Fonctions omp_set_lock and omp_set_nest_lock

Chacune de ces fonctions bloque le thread qui exécute la fonction jusqu'à ce que le verrou spécifié n’est disponible et qu’il définit ensuite le verrou. Un verrou simple est disponible si elle est déverrouillée. Un verrou pouvant être est disponible s’il est déverrouillé, ou si elle est déjà détenu par le thread qui exécute la fonction. Le format est le suivant :

```
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Pour un verrou simple, l’argument à la `omp_set_lock` fonction doit pointer vers une variable initialisée de verrou. La propriété du verrou est accordée au thread d’exécuter la fonction.

Pour un verrou pouvant être imbriqué, l’argument à la `omp_set_nest_lock` fonction doit pointer vers une variable initialisée de verrou. Le nombre d’imbrication est incrémenté et le thread est accordé ou conserve, la propriété du verrou.