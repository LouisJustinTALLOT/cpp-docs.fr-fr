---
description: 'En savoir plus sur : 3. Fonctions de la bibliothèque du runtime'
title: 3. Fonctions de la bibliothèque du runtime
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 67eb3b25efd65dcb99cd140bdc4e93491bacd79a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342554"
---
# <a name="3-run-time-library-functions"></a>3. fonctions de la bibliothèque Runtime

Cette section décrit les fonctions de la bibliothèque Runtime C et C++ OpenMP. L’en-tête **\<omp.h>** déclare deux types, plusieurs fonctions qui peuvent être utilisées pour contrôler et interroger l’environnement d’exécution parallèle, et des fonctions de verrouillage qui peuvent être utilisées pour synchroniser l’accès aux données.

Le type `omp_lock_t` est un type d’objet capable de représenter le fait qu’un verrou est disponible ou qu’un thread possède un verrou. Ces verrous sont appelés *verrous simples*.

Le type `omp_nest_lock_t` est un type d’objet capable de représenter soit qu’un verrou est disponible, soit à la fois l’identité du thread qui détient le verrou et un *nombre d’imbrications* (décrite ci-dessous). Ces verrous sont appelés *verrous imbriqués*.

Les fonctions de bibliothèque sont des fonctions externes avec une liaison « C ».

Les descriptions de ce chapitre sont réparties dans les rubriques suivantes :

- [Fonctions de l’environnement d’exécution](#31-execution-environment-functions)
- [Fonctions de verrouillage](#32-lock-functions)
- [Routines de minutage](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3,1 fonctions de l’environnement d’exécution

Les fonctions décrites dans cette section affectent et analysent les threads, les processeurs et l’environnement parallèle :

- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_get_max_threads](#313-omp_get_max_threads-function)
- [omp_get_thread_num](#314-omp_get_thread_num-function)
- [omp_get_num_procs](#315-omp_get_num_procs-function)
- [omp_in_parallel](#316-omp_in_parallel-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [omp_get_dynamic](#318-omp_get_dynamic-function)
- [omp_set_nested](#319-omp_set_nested-function)
- [omp_get_nested](#3110-omp_get_nested-function)

### <a name="311-omp_set_num_threads-function"></a><a name="311-omp_set_num_threads-function"></a> 3.1.1 omp_set_num_threads fonction

La `omp_set_num_threads` fonction définit le nombre de threads par défaut à utiliser pour les régions parallèles ultérieures qui ne spécifient pas de `num_threads` clause. au format suivant :

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

La valeur du paramètre *num_threads* doit être un entier positif. Son effet varie selon que l’ajustement dynamique du nombre de threads est activé. Pour obtenir un ensemble complet de règles sur l’interaction entre la `omp_set_num_threads` fonction et l’ajustement dynamique des threads, consultez la [section 2,3](2-directives.md#23-parallel-construct).

Cette fonction a les effets décrits ci-dessus quand elle est appelée à partir d’une partie du programme où la `omp_in_parallel` fonction retourne zéro. Si elle est appelée à partir d’une partie du programme où la `omp_in_parallel` fonction retourne une valeur différente de zéro, le comportement de cette fonction n’est pas défini.

Cet appel est prioritaire sur la `OMP_NUM_THREADS` variable d’environnement. La valeur par défaut pour le nombre de threads, qui peut être établi en appelant `omp_set_num_threads` ou en définissant la `OMP_NUM_THREADS` variable d’environnement, peut être substituée explicitement sur une `parallel` directive unique en spécifiant la `num_threads` clause.

Pour plus d’informations, consultez [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Références croisées

- [omp_set_dynamic](#317-omp_set_dynamic-function) fonction)
- [omp_get_dynamic](#318-omp_get_dynamic-function) fonction)
- Variable d’environnement [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- clause [num_threads](2-directives.md#23-parallel-construct)

### <a name="312-omp_get_num_threads-function"></a><a name="312-omp_get_num_threads-function"></a> 3.1.2 omp_get_num_threads fonction

La `omp_get_num_threads` fonction retourne le nombre de threads actuellement dans l’équipe qui exécute la région parallèle à partir de laquelle elle est appelée. au format suivant :

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

La `num_threads` clause, la `omp_set_num_threads` fonction et la `OMP_NUM_THREADS` variable d’environnement contrôlent le nombre de threads dans une équipe.

Si le nombre de threads n’a pas été explicitement défini par l’utilisateur, la valeur par défaut est définie par l’implémentation. Cette fonction crée une liaison avec la directive englobante la plus proche `parallel` . En cas d’appel à partir d’une partie série d’un programme, ou à partir d’une région parallèle imbriquée sérialisée, cette fonction retourne 1.

Pour plus d’informations, consultez [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Références croisées

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a><a name="313-omp_get_max_threads-function"></a> 3.1.3 omp_get_max_threads fonction

La `omp_get_max_threads` fonction retourne un entier qui est garanti au moins aussi grand que le nombre de threads qui seraient utilisés pour former une équipe si une région parallèle sans `num_threads` clause devait être affichée à ce stade du code. au format suivant :

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

L’exemple suivant exprime une limite inférieure de la valeur de `omp_get_max_threads` :

> *threads-utilisé-pour-Next-Team* <= `omp_get_max_threads`

Notez que si une autre région parallèle utilise la `num_threads` clause pour demander un nombre spécifique de threads, la garantie sur la limite inférieure du résultat de `omp_get_max_threads` n’est plus valable.

La `omp_get_max_threads` valeur de retour de la fonction peut être utilisée pour allouer dynamiquement un espace de stockage suffisant pour tous les threads de l’équipe formés à la région parallèle suivante.

#### <a name="cross-references"></a>Références croisées

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a><a name="314-omp_get_thread_num-function"></a> 3.1.4 omp_get_thread_num fonction

La `omp_get_thread_num` fonction retourne le numéro de thread, au sein de son équipe, du thread qui exécute la fonction. Le numéro de thread se situe entre 0 et `omp_get_num_threads()` -1, inclus. Le thread principal de l’équipe est le thread 0.

au format suivant :

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

En cas d’appel à partir d’une région de série, `omp_get_thread_num` retourne 0. En cas d’appel à partir d’une région parallèle imbriquée sérialisée, cette fonction retourne 0.

#### <a name="cross-references"></a>Références croisées

- [omp_get_num_threads](#312-omp_get_num_threads-function) fonction)

### <a name="315-omp_get_num_procs-function"></a><a name="315-omp_get_num_procs-function"></a> fonction de omp_get_num_procs 3.1.5

La `omp_get_num_procs` fonction retourne le nombre de processeurs qui sont disponibles pour le programme au moment où la fonction est appelée. au format suivant :

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a><a name="316-omp_in_parallel-function"></a> 3.1.6 omp_in_parallel fonction)

La `omp_in_parallel` fonction retourne une valeur différente de zéro si elle est appelée dans l’étendue dynamique d’une région parallèle s’exécutant en parallèle ; sinon, elle retourne 0. au format suivant :

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

Cette fonction retourne une valeur différente de zéro quand elle est appelée à partir d’une région s’exécutant en parallèle, y compris les régions imbriquées qui sont sérialisées.

### <a name="317-omp_set_dynamic-function"></a><a name="317-omp_set_dynamic-function"></a> 3.1.7 omp_set_dynamic fonction)

La `omp_set_dynamic` fonction active ou désactive l’ajustement dynamique du nombre de threads disponibles pour l’exécution des régions parallèles. au format suivant :

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Si *dynamic_threads* correspond à une valeur différente de zéro, le nombre de threads utilisés pour l’exécution des régions parallèles à venir peut être ajusté automatiquement par l’environnement d’exécution pour utiliser au mieux les ressources système. Par conséquent, le nombre de threads spécifié par l’utilisateur est le nombre maximal de threads. Le nombre de threads dans l’équipe qui exécute une région parallèle reste fixe pour la durée de cette région parallèle et est signalé par la `omp_get_num_threads` fonction.

Si *dynamic_threads* prend la valeur 0, l’ajustement dynamique est désactivé.

Cette fonction a les effets décrits ci-dessus quand elle est appelée à partir d’une partie du programme où la `omp_in_parallel` fonction retourne zéro. Si elle est appelée à partir d’une partie du programme où la `omp_in_parallel` fonction retourne une valeur différente de zéro, le comportement de cette fonction n’est pas défini.

Un appel à `omp_set_dynamic` est prioritaire sur la `OMP_DYNAMIC` variable d’environnement.

La valeur par défaut pour l’ajustement dynamique des threads est définie par l’implémentation. Par conséquent, les codes utilisateur qui dépendent d’un nombre spécifique de threads pour une exécution correcte doivent désactiver explicitement les threads dynamiques. Les implémentations ne sont pas nécessaires pour offrir la possibilité d’ajuster dynamiquement le nombre de threads, mais elles sont nécessaires pour fournir l’interface pour prendre en charge la portabilité sur toutes les plateformes.

#### <a name="microsoft-specific"></a>Spécifique à Microsoft

La prise en charge actuelle de `omp_get_dynamic` et `omp_set_dynamic` est la suivante :

Le paramètre d’entrée de `omp_set_dynamic` n’affecte pas la stratégie de thread et ne modifie pas le nombre de threads. `omp_get_num_threads` retourne toujours soit le nombre défini par l’utilisateur, s’il est défini, soit le numéro de thread par défaut. Dans l’implémentation Microsoft actuelle, `omp_set_dynamic(0)` désactive le Threading dynamique afin que l’ensemble de threads existant puisse être réutilisé pour la région parallèle suivante. `omp_set_dynamic(1)` active le Threading dynamique en ignorant l’ensemble existant de threads et en créant un nouvel ensemble pour la région parallèle à venir. Le nombre de threads dans le nouvel ensemble est identique à celui de l’ancien jeu et est basé sur la valeur de retour de `omp_get_num_threads` . Par conséquent, pour de meilleures performances, utilisez `omp_set_dynamic(0)` pour réutiliser les threads existants.

#### <a name="cross-references"></a>Références croisées

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a><a name="318-omp_get_dynamic-function"></a> 3.1.8 omp_get_dynamic fonction)

La `omp_get_dynamic` fonction retourne une valeur différente de zéro si l’ajustement dynamique des threads est activé et retourne 0 dans le cas contraire. au format suivant :

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

Si l’implémentation n’implémente pas l’ajustement dynamique du nombre de threads, cette fonction retourne toujours 0. Pour plus d’informations, consultez [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Références croisées

- Pour obtenir une description de l’ajustement dynamique des threads, consultez [omp_set_dynamic](#317-omp_set_dynamic-function).

### <a name="319-omp_set_nested-function"></a><a name="319-omp_set_nested-function"></a> 3.1.9 omp_set_nested fonction)

La `omp_set_nested` fonction active ou désactive le parallélisme imbriqué. au format suivant :

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

Si *Nested* prend la valeur 0, le parallélisme imbriqué est désactivé, ce qui correspond à la valeur par défaut, et les régions parallèles imbriquées sont sérialisées et exécutées par le thread actuel. Dans le cas contraire, le parallélisme imbriqué est activé et les régions parallèles imbriquées peuvent déployer des threads supplémentaires pour former des équipes imbriquées.

Cette fonction a les effets décrits ci-dessus quand elle est appelée à partir d’une partie du programme où la `omp_in_parallel` fonction retourne zéro. Si elle est appelée à partir d’une partie du programme où la `omp_in_parallel` fonction retourne une valeur différente de zéro, le comportement de cette fonction n’est pas défini.

Cet appel est prioritaire sur la `OMP_NESTED` variable d’environnement.

Lorsque le parallélisme imbriqué est activé, le nombre de threads utilisés pour exécuter des régions parallèles imbriquées est défini par l’implémentation. Par conséquent, les implémentations conformes à OpenMP sont autorisées à sérialiser des régions parallèles imbriquées même lorsque le parallélisme imbriqué est activé.

#### <a name="cross-references"></a>Références croisées

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a><a name="3110-omp_get_nested-function"></a> 3.1.10 omp_get_nested fonction)

La `omp_get_nested` fonction retourne une valeur différente de zéro si le parallélisme imbriqué est activé et 0 si elle est désactivée. Pour plus d’informations sur le parallélisme imbriqué, consultez [omp_set_nested](#319-omp_set_nested-function). au format suivant :

```cpp
#include <omp.h>
int omp_get_nested(void);
```

Si une implémentation n’implémente pas de parallélisme imbriqué, cette fonction retourne toujours 0.

## <a name="32-lock-functions"></a>3,2 fonctions de verrouillage

Les fonctions décrites dans cette section manipulent les verrous utilisés pour la synchronisation.

Pour les fonctions suivantes, la variable Lock doit avoir le type `omp_lock_t` . Cette variable doit être accessible uniquement par le biais de ces fonctions. Toutes les fonctions de verrouillage requièrent un argument qui a un pointeur vers le `omp_lock_t` type.

- La fonction [omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) Initialise un verrou simple.
- La fonction [omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) supprime un verrou simple.
- La fonction [omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) attend jusqu’à ce qu’un verrou simple soit disponible.
- La fonction [omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) libère un verrou simple.
- La fonction [omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) teste un verrou simple.

Pour les fonctions suivantes, la variable Lock doit avoir le type `omp_nest_lock_t` .  Cette variable doit être accessible uniquement par le biais de ces fonctions. Toutes les fonctions de verrouillage imbriquées requièrent un argument qui a un pointeur vers le `omp_nest_lock_t` type.

- La fonction [omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) Initialise un verrou imbriqué.
- La fonction [omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) supprime un verrou imbriqué.
- La fonction [omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) attend jusqu’à ce qu’un verrou imbriqué soit disponible.
- La fonction [omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) libère un verrou imbriqué.
- La fonction [omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) teste un verrou imbriqué.

Les fonctions de verrouillage OpenMP accèdent à la variable Lock de manière à toujours lire et mettre à jour la valeur la plus récente de la variable Lock. Par conséquent, il n’est pas nécessaire qu’un programme OpenMP inclue des directives explicites `flush` pour s’assurer que la valeur de la variable de verrou est cohérente entre les différents threads. (Il peut être nécessaire d’avoir des `flush` directives pour rendre les valeurs d’autres variables cohérentes.)

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a><a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a> 3.2.1 omp_init_lock et fonctions omp_init_nest_lock

Ces fonctions fournissent le seul moyen d’initialiser un verrou. Chaque fonction initialise le verrou associé au *verrou* de paramètre pour une utilisation dans les appels à venir. au format suivant :

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

L’état initial est déverrouillé (autrement dit, aucun thread ne possède le verrou). Pour un verrou imbriqué, le nombre initial d’imbrications est égal à zéro. Il n’est pas conforme d’appeler l’une de ces routines avec une variable Lock qui a déjà été initialisée.

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a><a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a> 3.2.2 omp_destroy_lock et fonctions omp_destroy_nest_lock

Ces fonctions permettent de s’assurer que le *verrou* de la variable pointé de verrouillage n’est pas initialisé. au format suivant :

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

Il n’est pas conforme d’appeler l’une de ces routines avec une variable Lock qui n’est pas initialisée ou déverrouillée.

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a><a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a> 3.2.3 omp_set_lock et fonctions omp_set_nest_lock

Chacune de ces fonctions bloque le thread qui exécute la fonction jusqu’à ce que le verrou spécifié soit disponible, puis définit le verrou. Un verrou simple est disponible s’il est déverrouillé. Un verrou imbriqué est disponible s’il est déverrouillé ou s’il est déjà détenu par le thread qui exécute la fonction. au format suivant :

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Pour un verrou simple, l’argument de la `omp_set_lock` fonction doit pointer vers une variable Lock initialisée. La propriété du verrou est accordée au thread qui exécute la fonction.

Pour un verrou imbriqué, l’argument de la `omp_set_nest_lock` fonction doit pointer vers une variable de verrou initialisée. Le nombre d’imbrications est incrémenté, et le thread est autorisé ou conserve la propriété du verrou.

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a><a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a> 3.2.4 omp_unset_lock et fonctions omp_unset_nest_lock

Ces fonctions permettent de libérer la propriété d’un verrou. au format suivant :

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

L’argument de chacune de ces fonctions doit pointer vers une variable de verrou initialisée détenue par le thread qui exécute la fonction. Le comportement n’est pas défini si le thread ne possède pas ce verrou.

Pour un verrou simple, la `omp_unset_lock` fonction libère le thread qui exécute la fonction de la propriété du verrou.

Pour un verrou imbriqué, la `omp_unset_nest_lock` fonction décrémente le nombre d’imbrications et libère le thread qui exécute la fonction de la propriété du verrou si le nombre résultant est égal à zéro.

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a><a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a> 3.2.5 omp_test_lock et fonctions omp_test_nest_lock

Ces fonctions essaient de définir un verrou, mais ne bloquent pas l’exécution du thread. au format suivant :

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

L’argument doit pointer vers une variable Lock initialisée. Ces fonctions essaient de définir un verrou de la même manière que `omp_set_lock` et `omp_set_nest_lock` , à ceci près qu’elles ne bloquent pas l’exécution du thread.

Pour un verrou simple, la `omp_test_lock` fonction retourne une valeur différente de zéro si le verrou est correctement défini ; sinon, elle retourne zéro.

Pour un verrou imbriqué, la `omp_test_nest_lock` fonction retourne le nouveau nombre d’imbrications si le verrou a été défini avec succès ; sinon, elle retourne zéro.

## <a name="33-timing-routines"></a>3,3 routines de minutage

Les fonctions décrites dans cette section prennent en charge un minuteur d’horloge murale portable :

- La fonction [omp_get_wtime](#331-omp_get_wtime-function) retourne le temps horloge écoulé.
- La fonction [omp_get_wtick](#332-omp_get_wtick-function) retourne des secondes entre les battements d’horloge successifs.

### <a name="331-omp_get_wtime-function"></a><a name="331-omp_get_wtime-function"></a> fonction omp_get_wtime 3.3.1

La `omp_get_wtime` fonction retourne une valeur à virgule flottante double précision égale à la durée d’horloge écoulée en secondes depuis une certaine « heure dans le passé ».  Le « temps passé » réel est arbitraire, mais il est garanti qu’il ne change pas pendant l’exécution du programme d’application. au format suivant :

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

Il est prévu que la fonction sera utilisée pour mesurer les durées écoulées, comme indiqué dans l’exemple suivant :

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Les heures retournées sont « horaires par thread », ce qui signifie qu’elles ne doivent pas être globalement cohérentes dans tous les threads qui participent à une application.

### <a name="332-omp_get_wtick-function"></a><a name="332-omp_get_wtick-function"></a> 3.3.2 omp_get_wtick fonction

La `omp_get_wtick` fonction retourne une valeur à virgule flottante double précision égale au nombre de secondes entre les battements d’horloge successifs. au format suivant :

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
