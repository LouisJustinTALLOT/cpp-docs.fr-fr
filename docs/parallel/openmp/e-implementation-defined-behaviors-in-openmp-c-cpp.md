---
title: E. Comportements définis par l’implémentation dans OpenMP C/C++
ms.date: 11/04/2016
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: 704062f36102a06e6e7b8cf015f6330f925a6bba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619347"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. Comportements définis par l’implémentation dans OpenMP C/C++

Cette annexe résume les comportements qui sont décrites en tant que « défini par l’implémentation » dans cette API.  Chaque comportement est référencé dans sa description dans la spécification principale.

## <a name="remarks"></a>Notes

Une implémentation est requise pour définir et documenter son comportement dans ces cas, mais cette liste peut être incomplète.

- **Nombre de threads :** si une région parallèle est rencontrée pendant que l’ajustement dynamique du nombre de threads est désactivé, et le nombre de threads demandé pour la région parallèle dépasse le nombre que le système d’exécution peut fournir, le comportement de le programme est défini par l’implémentation (voir la page 9).

   Dans Visual C++, pour une région parallèle non imbriqués, 64 threads (maximum) seront fournies.

- **Nombre de processeurs :** le nombre de processeurs physiques hébergeant les threads à un moment donné est défini par l’implémentation (voir la page 10).

   Dans Visual C++, ce nombre n’est pas constant et est contrôlé par le système d’exploitation.

- **Création d’équipes de threads :** le nombre de threads dans une équipe qui s’exécutent une région parallèle imbriquée est défini par l’implémentation. () consultez la page 10).

   Dans Visual C++, cela est déterminé par le système d’exploitation.

- **Schedule (Runtime) :** la décision en matière de planification est différée jusqu'à l’exécution. La taille de segment et de type de planification peut être choisie au moment de l’exécution en définissant le `OMP_SCHEDULE` variable d’environnement. Si cette variable d’environnement n’est pas définie, la planification qui en résulte est défini par l’implémentation (voir la page 13).

   Dans Visual C++, le type de planification est `static` avec aucune taille de segment.

- **Planification par défaut :** en l’absence de la clause de planification, la planification par défaut est défini par l’implémentation (voir la page 13).

   Dans Visual C++, le type de planification par défaut est `static` avec aucune taille de segment.

- **ATOMIQUE :** il est défini par l’implémentation si une implémentation remplace tous les `atomic` directives avec **critique** directives qui ont le même nom unique (voir la page de 20).

   Dans Visual C++, si les données modifiées par [atomique](../../parallel/openmp/reference/atomic.md) n’est pas sur un alignement naturel ou si elle est 1 ou 2 octets durée pendant laquelle toutes les opérations atomiques qui répondent à cette propriété utilise une section critique. Sinon, les sections critiques ne seront pas utilisées.

- **omp_get_num_threads :** si le nombre de threads n’a pas été explicitement défini par l’utilisateur, la valeur par défaut est défini par l’implémentation (consultez la page 9, et [Section 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) sur page 37).

   Dans Visual C++, le nombre de threads par défaut est égal au nombre de processeurs.

- **omp_set_dynamic :** la valeur par défaut pour l’ajustement de thread dynamique est défini par l’implémentation (voir [Section 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) sur la page 39).

   Dans Visual C++, la valeur par défaut est `FALSE`.

- **omp_set_nested :** lorsque parallélisme imbriquée est activée, le nombre de threads utilisés pour exécuter des zones imbriquées parallèles est défini par l’implémentation (voir [Section 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) sur la page 40).

   Dans Visual C++, le nombre de threads est déterminé par le système d’exploitation.

- `OMP_SCHEDULE` variable d’environnement : la valeur par défaut pour cette variable d’environnement est défini par l’implémentation (voir [Section 4.1](../../parallel/openmp/4-1-omp-schedule.md) page 48).

   Dans Visual C++, le type de planification est `static` avec aucune taille de segment.

- `OMP_NUM_THREADS` variable d’environnement : si aucune valeur n’est spécifiée pour le `OMP_NUM_THREADS` variable d’environnement, ou si la valeur spécifiée n’est pas un entier positif, ou si la valeur est supérieure au nombre maximal de threads que le système peut prendre en charge, le nombre de threads à utiliser défini par l’implémentation (voir [Section 4.2](../../parallel/openmp/4-2-omp-num-threads.md) page 48).

   Dans Visual C++, si la valeur spécifiée est égale à zéro ou moins, le nombre de threads est égal au nombre de processeurs.  Si la valeur est supérieure à 64, le nombre de threads est 64.

- `OMP_DYNAMIC` variable d’environnement : la valeur par défaut est défini par l’implémentation (voir [Section 4.3](../../parallel/openmp/4-3-omp-dynamic.md) page 49).

   Dans Visual C++, la valeur par défaut est `FALSE`.