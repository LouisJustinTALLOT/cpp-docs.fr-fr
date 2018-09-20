---
title: 3.1.9 fonction omp_set_nested | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e4afc3aa-bb96-4314-9849-fd5df5f437d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68e5898b8b57814a152ca2ce9ced84a9df8190cc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414535"
---
# <a name="319-ompsetnested-function"></a>3.1.9 Fonction omp_set_nested

Le **omp_set_nested** fonction active ou désactive le parallélisme imbriqué. Le format est le suivant :

```
#include <omp.h>
void omp_set_nested(int nested);
```

Si *imbriquée* prend la valeur 0, imbriqués parallélisme est désactivé, ce qui est la valeur par défaut, et les régions parallèles imbriquées sont sérialisées et exécutées par le thread actuel. Si *imbriquée* évalue une valeur différente de zéro, parallélisme imbriquée est activée, et des régions parallèles imbriquées peuvent déployer des threads supplémentaires pour former des équipes imbriquées.

Cette fonction a les effets décrits ci-dessus, lorsqu’elle est appelée à partir d’une partie du programme où la **omp_in_parallel** fonction retourne zéro. Si elle est appelée à partir d’une partie du programme où la **omp_in_parallel** fonction retourne une valeur différente de zéro, le comportement de cette fonction n’est pas défini.

Cet appel est prioritaire sur la **OMP_NESTED** variable d’environnement.

Lorsque le parallélisme imbriquée est activée, le nombre de threads utilisés pour exécuter des zones imbriquées parallèles est défini par l’implémentation. Par conséquent, les implémentations conformes OpenMP sont autorisées à sérialiser des régions parallèles imbriquées, même lorsque le parallélisme imbriquée est activée.

## <a name="cross-references"></a>Références externes :

- **OMP_NESTED** voir variable d’environnement [Section 4.4](../../parallel/openmp/4-4-omp-nested.md) page 49.

- **omp_in_parallel** de fonction, consultez [Section 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) sur page 38.