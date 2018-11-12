---
title: 4.3 OMP_DYNAMIC
ms.date: 11/04/2016
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
ms.openlocfilehash: 0ea6784159a11fc194d0c1cd16d2316a80b9cd37
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488563"
---
# <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC

Le **OMP_DYNAMIC** variable d’environnement Active ou désactive l’ajustement dynamique du nombre de threads disponibles pour l’exécution des régions parallèles, sauf si l’ajustement dynamique est explicitement activé ou désactivé en appelant le **omp_set_dynamic** routine de bibliothèque. Sa valeur doit être **TRUE** ou **FALSE**.

Si la valeur **TRUE**, le nombre de threads qui sont utilisés pour l’exécution des régions parallèles peut-être être modifiée par l’environnement d’exécution pour mieux exploiter les ressources système.  Si la valeur **FALSE**, ajustement dynamique est désactivée. La condition par défaut est défini par l’implémentation.

Exemple :

```
setenv OMP_DYNAMIC TRUE
```

## <a name="cross-references"></a>Références externes :

- Pour plus d’informations sur les régions parallèles, consultez [Section 2.3](../../parallel/openmp/2-3-parallel-construct.md) page 8.

- **omp_set_dynamic** de fonction, consultez [Section 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) sur la page 39.