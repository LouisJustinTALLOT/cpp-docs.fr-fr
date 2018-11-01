---
title: 4.4 OMP_NESTED
ms.date: 11/04/2016
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
ms.openlocfilehash: e45b8901c56923ab37ca387a5f057c5b41af21f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453619"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED

Le `OMP_NESTED` variable d’environnement Active ou désactive le parallélisme imbriquée à moins que le parallélisme imbriqué est activé ou désactivé en appelant le `o` **mp_set_nested** routine de bibliothèque. Si la valeur **TRUE**, parallélisme imbriquée est activée ; si elle est définie sur **FALSE**imbriquée parallélisme est désactivé. La valeur par défaut est **FALSE**.

Exemple :

```
setenv OMP_NESTED TRUE
```

## <a name="cross-reference"></a>Référence croisée :

- `omp_set_nested` fonction, consultez [Section 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) sur la page 40.