---
title: 3.1.8 Fonction omp_get_dynamic
ms.date: 11/04/2016
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
ms.openlocfilehash: d9476894e5aff4cc7bb9c67fbbeb14d185b65f5e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566424"
---
# <a name="318-ompgetdynamic-function"></a>3.1.8 Fonction omp_get_dynamic

Le **omp_get_dynamic** fonction retourne une valeur différente de zéro si l’ajustement dynamique de threads est activé et sinon, retourne 0. Le format est le suivant :

```
#include <omp.h>
int omp_get_dynamic(void);
```

Si l’implémentation n’implémente pas l’ajustement dynamique du nombre de threads, cette fonction retourne toujours 0.

## <a name="cross-references"></a>Références externes :

- Pour obtenir une description de l’ajustement de thread dynamique, consultez [Section 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) sur la page 39.