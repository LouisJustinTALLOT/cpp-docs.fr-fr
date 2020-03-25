---
title: E. Comportements définis par l’implémentation dans OpenMP C/C++
ms.date: 01/22/2019
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: e866eee9c6d85e93388f9f1d086badf948e2600e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215044"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. Comportements définis par l’implémentation dans OpenMP C/C++

Cette annexe résume les comportements qui sont décrits comme « définis par l’implémentation » dans cette API.  Chaque comportement fait l’inverse d’une référence croisée à sa description dans la spécification principale.

## <a name="remarks"></a>Notes

Une implémentation est requise pour définir et documenter son comportement dans ces cas-là, mais cette liste peut être incomplète.

- **Nombre de threads :** Si une région parallèle est rencontrée alors que l’ajustement dynamique du nombre de threads est désactivé et que le nombre de threads demandés pour la région parallèle est supérieur au nombre que le système d’exécution peut fournir, le comportement du programme est défini par l’implémentation (voir la page 9).

   Dans Visual C++, pour une région parallèle non imbriquée, 64 threads (le maximum) seront fournis.

- **Nombre de processeurs :** Le nombre de processeurs physiques qui hébergent réellement les threads à un moment donné est défini par l’implémentation (voir la page 10).

   En Visual C++, ce nombre n’est pas constant et est contrôlé par le système d’exploitation.

- **Création d’équipes de threads :** Le nombre de threads dans une équipe qui exécutent une région parallèle imbriquée est défini par l’implémentation (voir la page 10).

   En Visual C++, ce nombre est déterminé par le système d’exploitation.

- **planification (Runtime) :** La décision relative à la planification est différée jusqu’au moment de l’exécution. Vous pouvez choisir le type de planification et la taille de segment au moment de l’exécution en définissant la variable d’environnement `OMP_SCHEDULE`. Si cette variable d’environnement n’est pas définie, la planification qui en résulte est définie par l’implémentation (voir la page 13).

   En Visual C++, le type de planification est `static` sans taille de segment.

- **Planification par défaut :** En l’absence de la clause Schedule, la planification par défaut est définie par l’implémentation (voir la page 13).

   Dans Visual C++, le type de planification par défaut est `static` sans taille de segment.

- **Atomic :** Elle est définie par l’implémentation si une implémentation remplace toutes les directives `atomic` par des directives `critical` qui portent le même nom unique (voir la page 20).

   En Visual C++, si les données modifiées par [Atomic](reference/openmp-directives.md#atomic) ne se trouvent pas sur un alignement naturel ou s’il s’agit d’un ou de deux octets, toutes les opérations atomiques qui satisfont à cette propriété utiliseront une section critique. Dans le cas contraire, les sections critiques ne seront pas utilisées.

- **[omp_get_num_threads](3-run-time-library-functions.md#312-omp_get_num_threads-function):** Si le nombre de threads n’a pas été explicitement défini par l’utilisateur, la valeur par défaut est définie par l’implémentation (voir la page 9).

   En Visual C++, le nombre de threads par défaut est égal au nombre de processeurs.

- **[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function):** La valeur par défaut pour l’ajustement dynamique des threads est définie par l’implémentation.

   En Visual C++, la valeur par défaut est `FALSE`.

- **[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function):** Lorsque le parallélisme imbriqué est activé, le nombre de threads utilisés pour exécuter des régions parallèles imbriquées est défini par l’implémentation.

   En Visual C++, le nombre de threads est déterminé par le système d’exploitation.

- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule) variable d’environnement : la valeur par défaut de cette variable d’environnement est définie par l’implémentation.

   En Visual C++, le type de planification est `static` sans taille de segment.

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) variable d’environnement : si aucune valeur n’est spécifiée pour la variable d’environnement `OMP_NUM_THREADS`, ou si la valeur spécifiée n’est pas un entier positif, ou si la valeur est supérieure au nombre maximal de threads que le système peut prendre en charge, le nombre de threads à utiliser est défini par l’implémentation.

   En Visual C++, si la valeur spécifiée est inférieure ou égale à zéro, le nombre de threads est égal au nombre de processeurs.  Si la valeur est supérieure à 64, le nombre de threads est de 64.

- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) variable d’environnement : la valeur par défaut est définie par l’implémentation.

   En Visual C++, la valeur par défaut est `FALSE`.
