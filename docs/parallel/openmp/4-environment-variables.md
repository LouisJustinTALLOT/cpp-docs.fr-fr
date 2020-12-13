---
description: "En savoir plus sur : 4. Variables d'environnement"
title: 4. Variables d'environnement
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: 47c0d557497a387f89c13c88c414aae9eb9377ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342528"
---
# <a name="4-environment-variables"></a>4. variables d’environnement

Ce chapitre décrit les variables d’environnement de l’API C et C++ OpenMP (ou les mécanismes spécifiques de la plateforme) qui contrôlent l’exécution du code parallèle.  Les noms des variables d’environnement doivent être en majuscules. Les valeurs qui leur sont assignées ne respectent pas la casse et peuvent comporter des espaces blancs de début et de fin.  Les modifications apportées aux valeurs après le démarrage du programme sont ignorées.

Les variables d’environnement sont les suivantes :

- [OMP_SCHEDULE](#41-omp_schedule) définit le type de planification et la taille de segment au moment de l’exécution.
- [OMP_NUM_THREADS](#42-omp_num_threads) définit le nombre de threads à utiliser pendant l’exécution.
- [OMP_DYNAMIC](#43-omp_dynamic) active ou désactive l’ajustement dynamique du nombre de threads.
- [OMP_NESTED](#44-omp_nested) active ou désactive le parallélisme imbriqué.

Les exemples de ce chapitre montrent uniquement comment ces variables peuvent être définies dans des environnements UNIX C Shell (CSH). Dans les environnements Shell Korn et DOS, les actions sont similaires :

CSH  
`setenv OMP_SCHEDULE "dynamic"`

ksh  
`export OMP_SCHEDULE="dynamic"`

TERMINÉ  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a><a name="41-omp_schedule"></a> 4,1 OMP_SCHEDULE

`OMP_SCHEDULE` s’applique uniquement `for` aux `parallel for` directives et qui ont le type de planification `runtime` . Le type de planification et la taille de segment pour toutes ces boucles peuvent être définis au moment de l’exécution. Définissez cette variable d’environnement sur n’importe quel type de planification reconnu et sur un *chunk_size* facultatif.

Pour `for` les `parallel for` directives et qui ont un type de planification autre que `runtime` , `OMP_SCHEDULE` est ignoré. La valeur par défaut de cette variable d’environnement est définie par l’implémentation. Si la *chunk_size* facultative est définie, la valeur doit être positive. Si *chunk_size* n’est pas défini, la valeur 1 est utilisée, sauf lorsque la planification est `static` . Pour une `static` planification, la taille de segment par défaut est définie sur l’espace d’itération de la boucle divisé par le nombre de threads appliqués à la boucle.

Exemple :

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>Références croisées

- [pour](2-directives.md#241-for-construct) la directive
- [Parallel pour](2-directives.md#251-parallel-for-construct) la directive

## <a name="42-omp_num_threads"></a><a name="42-omp_num_threads"></a> 4,2 OMP_NUM_THREADS

La `OMP_NUM_THREADS` variable d’environnement définit le nombre de threads par défaut à utiliser pendant l’exécution. `OMP_NUM_THREADS` est ignoré si ce nombre est modifié explicitement en appelant la `omp_set_num_threads` routine de bibliothèque. Elle est également ignorée s’il existe une `num_threads` clause explicite sur une `parallel` directive.

La valeur de la `OMP_NUM_THREADS` variable d’environnement doit être un entier positif. Son effet varie selon que l’ajustement dynamique du nombre de threads est activé. Pour obtenir un ensemble complet de règles sur l’interaction entre la `OMP_NUM_THREADS` variable d’environnement et l’ajustement dynamique des threads, consultez la [section 2,3](2-directives.md#23-parallel-construct).

Le nombre de threads à utiliser est défini par l’implémentation si :

- la `OMP_NUM_THREADS` variable d’environnement n’est pas spécifiée.
- la valeur spécifiée n’est pas un entier positif ou
- la valeur est supérieure au nombre maximal de threads que le système peut prendre en charge.

Exemple :

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>Références croisées

- clause [num_threads](2-directives.md#23-parallel-construct)
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) fonction)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) fonction)

## <a name="43-omp_dynamic"></a><a name="43-omp_dynamic"></a> 4,3 OMP_DYNAMIC

La `OMP_DYNAMIC` variable d’environnement Active ou désactive l’ajustement dynamique du nombre de threads disponibles pour l’exécution des régions parallèles. `OMP_DYNAMIC` est ignoré lorsque l’ajustement dynamique est activé ou désactivé explicitement en appelant la `omp_set_dynamic` routine de bibliothèque. Sa valeur doit être `TRUE` ou `FALSE` .

Si `OMP_DYNAMIC` a la valeur `TRUE` , le nombre de threads utilisés pour l’exécution des régions parallèles peut être ajusté par l’environnement d’exécution pour utiliser au mieux les ressources système.  Si `OMP_DYNAMIC` a la valeur `FALSE` , l’ajustement dynamique est désactivé. La condition par défaut est définie par l’implémentation.

Exemple :

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>Références croisées

- [Régions parallèles](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) fonction)

## <a name="44-omp_nested"></a><a name="44-omp_nested"></a> 4,4 OMP_NESTED

La `OMP_NESTED` variable d’environnement Active ou désactive le parallélisme imbriqué, à moins que le parallélisme imbriqué soit activé ou désactivé en appelant la `omp_set_nested` routine de bibliothèque. Si `OMP_NESTED` a la valeur `TRUE` , le parallélisme imbriqué est activé. Si `OMP_NESTED` a la valeur `FALSE` , le parallélisme imbriqué est désactivé. La valeur par défaut est `FALSE`.

Exemple :

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>Référence croisée

- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) fonction)
