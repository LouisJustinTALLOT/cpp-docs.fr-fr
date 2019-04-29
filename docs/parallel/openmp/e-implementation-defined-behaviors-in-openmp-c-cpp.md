---
title: E. Comportements définis par l’implémentation dans OpenMP C/C++
ms.date: 01/22/2019
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: 3d8e9493cad1fce02e5d482cd5e612afb44bb37b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362752"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. Comportements définis par l’implémentation dans OpenMP C/C++

Cette annexe résume les comportements qui sont décrites en tant que « défini par l’implémentation » dans cette API.  Chaque comportement est référencé dans sa description dans la spécification principale.

## <a name="remarks"></a>Notes

Une implémentation est requise pour définir et documenter son comportement dans ces cas, mais cette liste peut être incomplète.

- **Nombre de threads :** Si une région parallèle est rencontrée pendant que l’ajustement dynamique du nombre de threads est désactivé, et le nombre de threads demandé pour la région parallèle est supérieur au nombre que le système d’exécution peut fournir, le comportement du programme est (consultez la page 9) défini par l’implémentation.

   Dans Visual C++, pour une région parallèle non imbriqués, 64 threads (maximum) seront fournies.

- **Nombre de processeurs :** Le nombre de processeurs physiques hébergeant les threads à un moment donné est défini par l’implémentation (voir la page 10).

   Dans Visual C++, ce nombre n’est pas constante et est contrôlé par le système d’exploitation.

- **Création d’équipes de threads :** Le nombre de threads dans une équipe qui s’exécutent une région parallèle imbriquée est défini par l’implémentation (voir la page 10).

   Dans Visual C++, ce nombre est déterminé par le système d’exploitation.

- **schedule(runtime):** La décision sur la planification est différée jusqu'à l’exécution. La taille de segment et de type de planification peut être choisie au moment de l’exécution en définissant le `OMP_SCHEDULE` variable d’environnement. Si cette variable d’environnement n’est pas définie, la planification qui en résulte est défini par l’implémentation (voir la page 13).

   Dans Visual C++, le type de planification est `static` avec aucune taille de segment.

- **Par défaut de planification :** En l’absence de la clause de planification, la planification par défaut est défini par l’implémentation (voir la page 13).

   Dans Visual C++, le type de planification par défaut est `static` avec aucune taille de segment.

- **ATOMIQUES :** Il est défini par l’implémentation si une implémentation remplace tous les `atomic` directives avec `critical` directives qui ont le même nom unique (voir la page de 20).

   Dans Visual C++, si les données modifiées par [atomique](reference/openmp-directives.md#atomic) n’est pas sur un alignement naturel ou s’il est long d’un ou deux octets, toutes les opérations atomiques qui répondent à cette propriété utilisera une section critique. Sinon, les sections critiques ne sera pas utilisées.

- **[omp_get_num_threads](3-run-time-library-functions.md#312-omp_get_num_threads-function):** Si le nombre de threads n’a pas été défini explicitement par l’utilisateur, la valeur par défaut est défini par l’implémentation (voir la page 9).

   Dans Visual C++, le nombre de threads par défaut est égal au nombre de processeurs.

- **[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function):** La valeur par défaut pour l’ajustement de thread dynamique est défini par l’implémentation.

   Dans Visual C++, la valeur par défaut est `FALSE`.

- **[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function):** Lorsque le parallélisme imbriquée est activée, le nombre de threads utilisés pour exécuter des zones imbriquées parallèles est défini par l’implémentation.

   Dans Visual C++, le nombre de threads est déterminé par le système d’exploitation.

- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule) variable d’environnement : La valeur par défaut pour cette variable d’environnement est défini par l’implémentation.

   Dans Visual C++, le type de planification est `static` avec aucune taille de segment.

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) variable d’environnement : Si aucune valeur n’est spécifiée pour le `OMP_NUM_THREADS` variable d’environnement, ou si la valeur spécifiée n’est pas un entier positif, ou si la valeur est supérieure au nombre maximal de threads que le système peut prendre en charge, le nombre de threads à utiliser est défini par l’implémentation.

   Dans Visual C++, si la valeur spécifiée est égale à zéro ou moins, le nombre de threads est égal au nombre de processeurs.  Si la valeur est supérieure à 64, le nombre de threads est 64.

- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) variable d’environnement : La valeur par défaut est défini par l’implémentation.

   Dans Visual C++, la valeur par défaut est `FALSE`.