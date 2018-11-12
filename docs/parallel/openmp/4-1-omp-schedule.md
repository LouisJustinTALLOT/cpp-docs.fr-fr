---
title: 4.1 OMP_SCHEDULE
ms.date: 11/04/2016
ms.assetid: d0dce411-2351-4ee9-a1cc-c0322a58b65c
ms.openlocfilehash: 4731299a4f7203dd01f660ea25bf2f5b58060630
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432693"
---
# <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE

**OMP_SCHEDULE** s’applique uniquement aux **pour** et **parallèles pour** directives qui ont le type de planification **runtime**. La taille de type et le segment de planification pour toutes les boucles de ce type peut être définie au moment de l’exécution en définissant cette variable d’environnement pour les types de planification reconnu et facultative *chunk_size*.

Pour **pour** et **parallèles pour** directives qui ont un type de planification autre que **runtime**, **OMP_SCHEDULE** est ignoré. La valeur par défaut pour cette variable d’environnement est défini par l’implémentation. Si le paramètre facultatif *chunk_size* est définie, la valeur doit être positive. Si *chunk_size* n’est pas défini, la valeur 1 est supposée, sauf dans le cas d’un **statique** planification. Pour un **statique** calendrier, la taille de segment par défaut est définie à l’espace d’itération de boucle divisé par le nombre de threads appliqué à la boucle.

Exemple :

```
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

## <a name="cross-references"></a>Références externes :

- **pour** directive, consultez [Section 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) à la page 11.

- **parallèle pour** directive, consultez [Section 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) page 16.