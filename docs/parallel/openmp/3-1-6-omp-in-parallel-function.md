---
title: 3.1.6 Fonction omp_in_parallel
ms.date: 11/04/2016
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
ms.openlocfilehash: 2f251cb994771278c7f4e3f50f01e02126f6f88d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482041"
---
# <a name="316-ompinparallel-function"></a>3.1.6 Fonction omp_in_parallel

Le **omp_in_parallel** fonction retourne une valeur différente de zéro si elle est appelée dans l’étendue dynamique d’une région parallèle s’exécutaient en parallèle ; sinon, elle retourne 0. Le format est le suivant :

```
#include <omp.h>
int omp_in_parallel(void);
```

Cette fonction retourne une valeur différente de zéro lorsque appelé à partir d’une région s’exécutant en parallèle, y compris des zones imbriquées qui sont sérialisés.