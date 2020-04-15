---
title: 4. Variables d'environnement
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: e93c59654c17ed6dbfb7483ac2dce716ce24b52a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370265"
---
# <a name="4-environment-variables"></a>4. Variables de l’environnement

Ce chapitre décrit les variables de l’environnement OpenMP C et CMD (ou des mécanismes spécifiques à la plate-forme similaires) qui contrôlent l’exécution du code parallèle.  Les noms des variables de l’environnement doivent être majuscules. Les valeurs qui leur sont assignées sont insensibles aux cas et peuvent avoir un espace blanc de premier plan et de fuite.  Les modifications apportées aux valeurs après le début du programme sont ignorées.

Les variables de l’environnement sont les suivantes :

- [OMP_SCHEDULE](#41-omp_schedule) définit le type d’horaire et la taille des morceaux.
- [OMP_NUM_THREADS](#42-omp_num_threads) définit le nombre de threads à utiliser pendant l’exécution.
- [OMP_DYNAMIC](#43-omp_dynamic) permet ou désactive l’ajustement dynamique du nombre de threads.
- [OMP_NESTED](#44-omp_nested) permet ou désactive le parallélisme imbriqué.

Les exemples de ce chapitre ne font que démontrer comment ces variables pourraient être définies dans les environnements de coquille Unix C (csh). Dans les environnements de la coque Korn et de DOS, les actions sont similaires :

Csh:  
`setenv OMP_SCHEDULE "dynamic"`

Ksh:  
`export OMP_SCHEDULE="dynamic"`

DOS:  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a><a name="41-omp_schedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE`ne s’applique qu’aux directives et `for` `parallel for` aux directives qui ont le type `runtime`d’horaire . Le type d’horaire et la taille du morceau pour toutes ces boucles peuvent être réglés au moment de l’exécution. Définissez cette variable d’environnement à n’importe quel type de calendrier reconnu et à un *chunk_size*facultatif.

Pour `for` `parallel for` et les directives qui `runtime`ont `OMP_SCHEDULE` un type d’horaire autre que , est ignoré. La valeur par défaut pour cette variable d’environnement est définie par implémentation. Si le *chunk_size* facultatif est défini, la valeur doit être positive. Si *chunk_size* n’est pas définie, une valeur de 1 est `static`supposée, sauf lorsque l’horaire est . Pour `static` un calendrier, la taille du morceau par défaut est réglée sur l’espace d’itération de boucle divisé par le nombre de threads appliqués à la boucle.

Exemple :

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>Références croisées

- [pour](2-directives.md#241-for-construct) la directive
- [parallèle pour](2-directives.md#251-parallel-for-construct) la directive

## <a name="42-omp_num_threads"></a><a name="42-omp_num_threads"></a>4,2 OMP_NUM_THREADS

La `OMP_NUM_THREADS` variable de l’environnement définit le nombre par défaut de threads à utiliser pendant l’exécution. `OMP_NUM_THREADS`est ignoré si ce numéro est `omp_set_num_threads` explicitement modifié en appelant la routine de la bibliothèque. Il est également ignoré s’il `num_threads` ya `parallel` une clause explicite sur une directive.

La valeur `OMP_NUM_THREADS` de la variable de l’environnement doit être un intégré positif. Son effet dépend de l’inseminage dynamique du nombre de threads activé. Pour un ensemble complet de règles `OMP_NUM_THREADS` sur l’interaction entre l’environnement variable et l’ajustement dynamique des threads, voir [la section 2.3](2-directives.md#23-parallel-construct).

Le nombre de threads à utiliser est défini par implémentation si :

- la `OMP_NUM_THREADS` variable de l’environnement n’est pas spécifiée,
- la valeur spécifiée n’est pas un intégré positif, ou
- la valeur est supérieure au nombre maximum de threads que le système peut prendre en charge.

Exemple :

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>Références croisées

- [clause num_threads](2-directives.md#23-parallel-construct)
- [fonction omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)
- [fonction omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)

## <a name="43-omp_dynamic"></a><a name="43-omp_dynamic"></a>4,3 OMP_DYNAMIC

La `OMP_DYNAMIC` variable de l’environnement permet ou désactive l’ajustement dynamique du nombre de threads disponibles pour l’exécution de régions parallèles. `OMP_DYNAMIC`est ignoré lorsque l’ajustement dynamique est `omp_set_dynamic` explicitement activé ou désactivé en appelant la routine de la bibliothèque. Sa valeur `TRUE` doit `FALSE`être ou .

Si `OMP_DYNAMIC` elle `TRUE`est configurée, le nombre de threads utilisés pour l’exécution des régions parallèles peut être ajusté par l’environnement de temps d’exécution pour utiliser au mieux les ressources du système.  Si `OMP_DYNAMIC` l’on s’y fixe, l’ajustement `FALSE`dynamique est désactivé. La condition par défaut est définie par implémentation.

Exemple :

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>Références croisées

- [Régions parallèles](2-directives.md#23-parallel-construct)
- [fonction omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)

## <a name="44-omp_nested"></a><a name="44-omp_nested"></a>4,4 OMP_NESTED

La `OMP_NESTED` variable d’environnement permet ou désactive le parallélisme imbriqué à moins que le parallélisme imbriqué ne soit activé ou désactivé en appelant la routine de la `omp_set_nested` bibliothèque. Si `OMP_NESTED` est `TRUE`réglé à , parallélisme imbriqué est activé. Si `OMP_NESTED` est `FALSE`réglé à , parallélisme imbriqué est désactivé. La valeur par défaut est `FALSE`.

Exemple :

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>Référence croisée

- [fonction omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)
