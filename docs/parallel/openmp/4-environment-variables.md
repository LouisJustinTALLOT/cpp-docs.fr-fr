---
title: 4. Variables d’environnement
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: 558b835c36253fb67339fba9b46cb0170dd6d1d0
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087195"
---
# <a name="4-environment-variables"></a>4. Variables d’environnement

Ce chapitre décrit les variables d’environnement OpenMP C et C++ API (ou les mécanismes spécifiques à la plateforme similaires) qui contrôlent l’exécution du code parallèle.  Les noms des variables d’environnement doivent être en majuscules. Les valeurs affectées à leur respectent la casse et peuvent avoir des espaces de début et de fin.  Modifications aux valeurs une fois que le programme a commencé sont ignorées.

Les variables d’environnement sont les suivantes :

- [OMP_SCHEDULE](#41-omp_schedule) définit la taille de segment et de type de planification de l’exécution.
- [OMP_NUM_THREADS](#42-omp_num_threads) définit le nombre de threads à utiliser lors de l’exécution.
- [OMP_DYNAMIC](#43-omp_dynamic) Active ou désactive l’ajustement dynamique du nombre de threads.
- [OMP_NESTED](#44-omp_nested) Active ou désactive le parallélisme imbriqué.

Les exemples dans ce chapitre montrent uniquement comment ces variables peuvent être définies dans les environnements Unix C shell (csh). Dans les environnements de déni de service et un environnement Korn, les actions sont similaires :

csh :  
`setenv OMP_SCHEDULE "dynamic"`

ksh :  
`export OMP_SCHEDULE="dynamic"`

DÉNI DE SERVICE :  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE` s’applique uniquement aux `for` et `parallel for` directives qui ont le type de planification `runtime`. La taille de type et le segment de planification pour toutes les boucles de ce type peut être définie au moment de l’exécution. Définissez cette variable d’environnement pour n’importe quel type de planification reconnu et facultative *chunk_size*.

Pour `for` et `parallel for` directives qui ont un type de planification autre que `runtime`, `OMP_SCHEDULE` est ignoré. La valeur par défaut pour cette variable d’environnement est défini par l’implémentation. Si le paramètre facultatif *chunk_size* est définie, la valeur doit être positive. Si *chunk_size* n’est pas définie, la valeur 1 est supposée, sauf lorsque la planification est `static`. Pour un `static` calendrier, la taille de segment par défaut est définie à l’espace d’itération de boucle divisé par le nombre de threads appliqué à la boucle.

Exemple :

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>Références croisées

- [pour](2-directives.md#241-for-construct) (directive)
- [parallèle pour](2-directives.md#251-parallel-for-construct) (directive)

## <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS

Le `OMP_NUM_THREADS` variable d’environnement définit le nombre de threads à utiliser lors de l’exécution par défaut. `OMP_NUM_THREADS` est ignoré si ce nombre est modifié explicitement en appelant le `omp_set_num_threads` routine de bibliothèque. Il est également ignoré s’il existe une explicite `num_threads` clause sur une `parallel` directive.

La valeur de la `OMP_NUM_THREADS` variable d’environnement doit être un entier positif. Son effet dépend de si l’ajustement dynamique du nombre de threads est activé. Pour un ensemble complet de règles sur l’interaction entre le `OMP_NUM_THREADS` environnement ajustement variable et dynamique de threads, consultez [section 2.3](2-directives.md#23-parallel-construct).

Le nombre de threads à utiliser est défini par l’implémentation si :

- le `OMP_NUM_THREADS` variable d’environnement n’est pas spécifiée,
- la valeur spécifiée n’est pas un entier positif, ou
- la valeur est supérieure au nombre maximal de threads que le système peut prendre en charge.

Exemple :

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>Références croisées

- [num_threads](2-directives.md#23-parallel-construct) clause
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) function
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) function

## <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC

Le `OMP_DYNAMIC` variable d’environnement Active ou désactive l’ajustement dynamique du nombre de threads disponibles pour l’exécution des régions parallèles. `OMP_DYNAMIC` est ignoré lors de l’ajustement dynamique est explicitement activé ou désactivé en appelant le `omp_set_dynamic` routine de bibliothèque. Sa valeur doit être `TRUE` ou `FALSE`.

Si `OMP_DYNAMIC` est défini sur `TRUE`, le nombre de threads qui sont utilisés pour l’exécution des régions parallèles peut-être être modifiée par l’environnement d’exécution sur l’utilisation des ressources système.  Si `OMP_DYNAMIC` a la valeur `FALSE`, ajustement dynamique est désactivée. La condition par défaut est défini par l’implémentation.

Exemple :

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>Références croisées

- [Régions parallèles](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) function

## <a name="44-ompnested"></a>4.4 OMP_NESTED

Le `OMP_NESTED` variable d’environnement Active ou désactive le parallélisme imbriquée à moins que le parallélisme imbriqué est activé ou désactivé en appelant le `omp_set_nested` routine de bibliothèque. Si `OMP_NESTED` a la valeur `TRUE`, parallélisme imbriquée est activée. Si `OMP_NESTED` a la valeur `FALSE`, imbriquée parallélisme est désactivé. La valeur par défaut est `FALSE`.

Exemple :

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>Références croisées

- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) (fonction)
