---
title: 3. Fonctions de bibliothèque du Run-time
ms.date: 01/17/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 4e72d2d74bb26f8eeeb422881cabf92630cced43
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363230"
---
# <a name="3-run-time-library-functions"></a>3. Fonctions de bibliothèque du Run-time

Cette section décrit les fonctions de bibliothèque du run-time OpenMP C et C++. L’en-tête  **\<omp.h >** déclare deux types, plusieurs fonctions qui peuvent être utilisées pour contrôler et interroger l’environnement d’exécution en parallèle et verrouiller les fonctions qui peuvent être utilisées pour synchroniser l’accès aux données.

Le type `omp_lock_t` est un type d’objet capable de représenter qu’un verrou est disponible, ou qu’un thread possède un verrou. Ces verrous sont appelés *verrous simples*.

Le type `omp_nest_lock_t` est un type d’objet capable de représenter qu’un verrou est disponible, ou l’identité du thread qui détient le verrou et un *imbrication nombre* (décrits ci-dessous). Ces verrous sont appelés *verrous pouvant être imbriqués*.

Les fonctions de bibliothèque sont des fonctions externes avec une liaison de « C ».

Les descriptions dans ce chapitre sont réparties dans les rubriques suivantes :

- [Fonctions de l’environnement d’exécution](#31-execution-environment-functions)
- [Fonctions de verrouillage](#32-lock-functions)
- [Routines de minutage](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 exécution des fonctions d’environnement

Les fonctions décrites dans cette section affectent et surveiller des threads, de processeurs et de l’environnement parallèle :

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

### <a name="311-ompsetnumthreads-function"></a>3.1.1 omp_set_num_threads (fonction)

Le `omp_set_num_threads` fonction définit le nombre par défaut de threads à utiliser pour ultérieurement à des régions parallèles, ne spécifient pas un `num_threads` clause. Le format est le suivant :

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

La valeur du paramètre *num_threads* doit être un entier positif. Son effet dépend de si l’ajustement dynamique du nombre de threads est activé. Pour un ensemble complet de règles sur l’interaction entre le `omp_set_num_threads` (fonction) et l’ajustement dynamique de threads, consultez [section 2.3](2-directives.md#23-parallel-construct).

Cette fonction a les effets décrits ci-dessus, lorsqu’elle est appelée à partir d’une partie du programme où la `omp_in_parallel` fonction retourne zéro. Si elle est appelée à partir d’une partie du programme où la `omp_in_parallel` fonction retourne une valeur différente de zéro, le comportement de cette fonction n’est pas défini.

Cet appel est prioritaire sur la `OMP_NUM_THREADS` variable d’environnement. La valeur par défaut pour le nombre de threads, ce qui peut être établie en appelant `omp_set_num_threads` ou en définissant le `OMP_NUM_THREADS` variable d’environnement, peuvent être substituées explicitement sur un seul `parallel` directive en spécifiant le `num_threads` clause.

#### <a name="cross-references"></a>Références croisées

- [omp_set_dynamic](#317-omp_set_dynamic-function) function
- [omp_get_dynamic](#318-omp_get_dynamic-function) function
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) variable d’environnement
- [num_threads](2-directives.md#23-parallel-construct) clause

### <a name="312-ompgetnumthreads-function"></a>3.1.2 omp_get_num_threads (fonction)

Le `omp_get_num_threads` fonction retourne le nombre de threads actuellement dans l’équipe de l’exécution de la région parallèle à partir de laquelle elle est appelée. Le format est le suivant :

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

Le `num_threads` clause, le `omp_set_num_threads` (fonction) et le `OMP_NUM_THREADS` variable d’environnement contrôler le nombre de threads dans une équipe.

Si le nombre de threads n’a pas été défini explicitement par l’utilisateur, la valeur par défaut est défini par l’implémentation. Cette fonction est liée à la forme plus proche `parallel` directive. Si elle est appelée à partir d’une série partie d’un programme ou à partir d’une région parallèle imbriquée qui est sérialisée, cette fonction retourne 1.

#### <a name="cross-references"></a>Références croisées

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-ompgetmaxthreads-function"></a>3.1.3 omp_get_max_threads (fonction)

Le `omp_get_max_threads` fonction retourne un entier qui a la garantie d’être au moins aussi grand que le nombre de threads qui serait utilisée pour former une équipe si une région parallèle sans un `num_threads` clause devait être vu à ce stade dans le code. Le format est le suivant :

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

Les éléments suivants exprimant une limite inférieure de la valeur de `omp_get_max_threads`:

```

threads-used-for-next-team
<= omp_get_max_threads
```

Notez que si un autre parallèle région utilise le `num_threads` clause pour demander un certain nombre de threads, la garantie de la limite inférieure du résultat de `omp_get_max_threads` aucun blocage long.

Le `omp_get_max_threads` valeur de retour de la fonction peut être utilisé pour allouer dynamiquement de stockage suffisant pour tous les threads dans l’équipe formé à la région parallèle suivante.

#### <a name="cross-references"></a>Références croisées

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num (fonction)

Le `omp_get_thread_num` fonction retourne le nombre de threads au sein de son équipe, du thread exécutant la fonction. Le se trouve de thread nombre compris entre 0 et `omp_get_num_threads()`-1, inclus. Le thread principal de l’équipe est 0.

Le format est le suivant :

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

Si elle est appelée à partir d’une région de série, `omp_get_thread_num` retourne 0. Si elle est appelée à partir de dans une région parallèle imbriquée qui est sérialisée, cette fonction retourne 0.

#### <a name="cross-references"></a>Références croisées

- [omp_get_num_threads](#312-omp_get_num_threads-function) function

### <a name="315-ompgetnumprocs-function"></a>3.1.5 omp_get_num_procs (fonction)

Le `omp_get_num_procs` fonction retourne le nombre de processeurs qui sont disponibles pour le programme au moment de la fonction est appelée. Le format est le suivant :

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel (fonction)

Le `omp_in_parallel` fonction retourne une valeur différente de zéro si elle est appelée dans l’étendue dynamique d’une région parallèle s’exécutaient en parallèle ; sinon, elle retourne 0. Le format est le suivant :

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

Cette fonction retourne une valeur différente de zéro lorsque appelé à partir d’une région s’exécutant en parallèle, y compris des zones imbriquées qui sont sérialisés.

### <a name="317-ompsetdynamic-function"></a>3.1.7 omp_set_dynamic (fonction)

Le `omp_set_dynamic` fonction active ou désactive l’ajustement dynamique du nombre de threads disponibles pour l’exécution des régions parallèles. Le format est le suivant :

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Si *dynamic_threads* évalue une valeur différente de zéro, le nombre de threads qui sont utilisés pour l’exécution des régions parallèles à venir peut être ajusté automatiquement par l’environnement d’exécution sur l’utilisation des ressources système. Par conséquent, le nombre de threads spécifié par l’utilisateur est le nombre maximal de threads. Le nombre de threads dans l’équipe de l’exécution d’une région parallèle reste fixe pendant la durée de cette région parallèle et est signalé par le `omp_get_num_threads` (fonction).

Si *dynamic_threads* prend la valeur 0, l’ajustement dynamique est désactivée.

Cette fonction a les effets décrits ci-dessus, lorsqu’elle est appelée à partir d’une partie du programme où la `omp_in_parallel` fonction retourne zéro. Si elle est appelée à partir d’une partie du programme où la `omp_in_parallel` fonction retourne une valeur différente de zéro, le comportement de cette fonction n’est pas défini.

Un appel à `omp_set_dynamic` est prioritaire sur la `OMP_DYNAMIC` variable d’environnement.

La valeur par défaut pour l’ajustement dynamique de threads est défini par l’implémentation. Par conséquent, les codes utilisateur qui dépendent d’un nombre spécifique de l’exécution correcte des threads doivent désactiver explicitement les threads dynamiques. Implémentations n’êtes pas obligées de fournir la possibilité d’ajuster dynamiquement le nombre de threads, mais elles sont requises pour fournir l’interface pour prendre en charge la portabilité sur toutes les plateformes.

#### <a name="cross-references"></a>Références croisées

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-ompgetdynamic-function"></a>3.1.8 omp_get_dynamic (fonction)

Le `omp_get_dynamic` fonction retourne une valeur différente de zéro si l’ajustement dynamique de threads est activé et sinon, retourne 0. Le format est le suivant :

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

Si l’implémentation n’implémente pas l’ajustement dynamique du nombre de threads, cette fonction retourne toujours 0.

#### <a name="cross-references"></a>Références croisées

- Pour obtenir une description de l’ajustement de thread dynamique, consultez [omp_set_dynamic](#317-omp_set_dynamic-function).

### <a name="319-ompsetnested-function"></a>3.1.9 omp_set_nested (fonction)

Le `omp_set_nested` fonction active ou désactive le parallélisme imbriqué. Le format est le suivant :

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

Si *imbriquée* prend la valeur 0, imbriqués parallélisme est désactivé, ce qui est la valeur par défaut, et les régions parallèles imbriquées sont sérialisées et exécutées par le thread actuel. Sinon, parallélisme imbriquée est activée, et des régions parallèles imbriquées peuvent déployer des threads supplémentaires pour former des équipes imbriquées.

Cette fonction a les effets décrits ci-dessus, lorsqu’elle est appelée à partir d’une partie du programme où la `omp_in_parallel` fonction retourne zéro. Si elle est appelée à partir d’une partie du programme où la `omp_in_parallel` fonction retourne une valeur différente de zéro, le comportement de cette fonction n’est pas défini.

Cet appel est prioritaire sur la `OMP_NESTED` variable d’environnement.

Lorsque le parallélisme imbriquée est activée, le nombre de threads utilisés pour exécuter des zones imbriquées parallèles est défini par l’implémentation. Par conséquent, les implémentations conformes OpenMP sont autorisées à sérialiser des régions parallèles imbriquées, même lorsque le parallélisme imbriquée est activée.

#### <a name="cross-references"></a>Références croisées

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested (fonction)

Le `omp_get_nested` fonction retourne une valeur différente de zéro si le parallélisme imbriquée est activée et 0 s’il est désactivé. Pour plus d’informations sur le parallélisme imbriquée, consultez [omp_set_nested](#319-omp_set_nested-function). Le format est le suivant :

```cpp
#include <omp.h>
int omp_get_nested(void);
```

Si une implémentation n’implémente pas parallélisme imbriqué, cette fonction retourne toujours 0.

## <a name="32-lock-functions"></a>3.2 fonctions de verrouillage

Les fonctions décrites dans cette section manipulent des verrous utilisés pour la synchronisation.

Pour les fonctions suivantes, la variable de verrou doit avoir le type `omp_lock_t`. Cette variable doit uniquement être accessible via ces fonctions. Toutes les fonctions de verrouillage nécessitent un argument qui a un pointeur vers `omp_lock_t` type.

- Le [fonctions omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) fonction initialise un verrou simple.
- Le [fonctions omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) fonction supprime un verrou simple.
- Le [omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) fonction attend un verrou simple est disponible.
- Le [fonctions omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) fonction libère un verrou simple.
- Le [fonctions omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) fonction teste un verrou simple.

Pour les fonctions suivantes, la variable de verrou doit avoir le type `omp_nest_lock_t`.  Cette variable doit uniquement être accessible via ces fonctions. Toutes les fonctions de verrou pouvant être nécessitent un argument qui a un pointeur vers `omp_nest_lock_t` type.

- Le [omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) fonction initialise un verrou pouvant être imbriqué.
- Le [omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) fonction supprime un verrou pouvant être imbriqué.
- Le [omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) fonction attend un verrou pouvant être disponible.
- Le [omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) fonction libère un verrou pouvant être imbriqué.
- Le [omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) fonction teste un verrou pouvant être imbriqué.

Les fonctions de verrouillage OpenMP accéder à la variable de verrou de sorte qu’ils toujours lire et mettre à jour la valeur la plus récente de la variable de verrou. Par conséquent, il n’est pas nécessaire pour un programme OpenMP inclure explicite `flush` directives pour vous assurer que la valeur de la variable de verrou est cohérente parmi différents threads. (Il peut être nécessaire pour `flush` directives pour rendre les valeurs des autres variables cohérents.)

### <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 fonctions fonctions omp_init_lock et omp_init_nest_lock

Ces fonctions vous permettent uniquement de l’initialisation d’un verrou. Chaque fonction initialise le verrou associé au paramètre *verrou* pour une utilisation dans les appels à venir. Le format est le suivant :

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

L’état initial est déverrouillé (autrement dit, aucun thread ne possède le verrou). Pour obtenir un verrou pouvant être imbriqué, le nombre initial d’imbrication est égal à zéro. Il n’est pas conforme à appeler une de ces routines avec une variable de verrou qui a déjà été initialisé.

### <a name="322-ompdestroylock-and-ompdestroynestlock-functions"></a>3.2.2 fonctions fonctions omp_destroy_lock et omp_destroy_nest_lock

Ces fonctions vous assurer que la verrouiller la variable référencée *verrou* n’est pas initialisée. Le format est le suivant :

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

Il est déverrouillé ou non conformes d’appeler une de ces routines avec une variable de verrou qui a non initialisé.

### <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 fonctions omp_set_lock et omp_set_nest_lock

Chacune de ces fonctions bloque le thread qui exécute la fonction jusqu'à ce que le verrou spécifié n’est disponible et qu’il définit ensuite le verrou. Un verrou simple est disponible s’il est déverrouillé. Un verrou pouvant être est disponible s’il est déverrouillé ou si elle est déjà détenu par le thread qui exécute la fonction. Le format est le suivant :

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Pour un verrou simple, l’argument à la `omp_set_lock` fonction doit pointer vers une variable initialisée de verrou. La propriété du verrou est accordée au thread d’exécuter la fonction.

Pour un verrou pouvant être imbriqué, l’argument à la `omp_set_nest_lock` fonction doit pointer vers une variable initialisée de verrou. Le nombre d’imbrication est incrémenté et le thread est accordé, ou si elle conserve, la propriété du verrou.

### <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 fonctions fonctions omp_unset_lock et omp_unset_nest_lock

Ces fonctions vous permettent de libérer la possession d’un verrou. Le format est le suivant :

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

L’argument de chacune de ces fonctions doit pointer vers une variable initialisée verrou détenue par le thread qui exécute la fonction. Le comportement est indéfini si le thread ne possède pas ce verrou.

Pour obtenir un verrou simple, le `omp_unset_lock` fonction libère le thread de l’exécution de la fonction à partir de la propriété du verrou.

Pour obtenir un verrou pouvant être imbriqué, le `omp_unset_nest_lock` fonction décrémente le nombre d’imbrication et les versions le thread qui exécute la fonction à partir de la propriété du verrou si le nombre résultant est égal à zéro.

### <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 fonctions fonctions omp_test_lock et omp_test_nest_lock

Ces fonctions essaient de définir un verrou, mais ne bloquent pas l’exécution du thread. Le format est le suivant :

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

L’argument doit pointer vers une variable initialisée de verrou. Ces fonctions essayez de définir un verrou de la même manière que `omp_set_lock` et `omp_set_nest_lock`, sauf qu’ils ne bloquent pas l’exécution du thread.

Pour obtenir un verrou simple, le `omp_test_lock` fonction retourne une valeur différente de zéro si le verrou est défini correctement ; sinon, elle retourne zéro.

Pour obtenir un verrou pouvant être imbriqué, le `omp_test_nest_lock` fonction retourne le nouveau nombre d’imbrication si le verrou est défini correctement ; sinon, elle retourne zéro.

## <a name="33-timing-routines"></a>3.3 routines de minutage

Les fonctions décrites dans cette section prennent en charge un minuteur d’horloge portable :

- Le [omp_get_wtime](#331-omp_get_wtime-function) fonction retourne le temps horloge écoulé.
- Le [omp_get_wtick](#332-omp_get_wtick-function) fonction retourne les secondes entre les battements d’horloge successives.

### <a name="331-ompgetwtime-function"></a>3.3.1 omp_get_wtime (fonction)

Le `omp_get_wtime` fonction retourne une valeur à virgule flottante double précision égale à la durée totale écoulée en secondes depuis « ultérieurement dans le passé ».  L’heure « réelle dans le passé » est arbitraire, mais il a ne peut ne pas changer pendant l’exécution du programme d’application. Le format est le suivant :

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

Il est prévu que la fonction sera être utilisée pour mesurer le temps écoulé comme indiqué dans l’exemple suivant :

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Les heures retournées sont « fois par thread » par qui est destinée qu’ils ne sont pas nécessairement être globalement cohérente sur tous les threads qui participent à une application.

### <a name="332-ompgetwtick-function"></a>3.3.2 omp_get_wtick (fonction)

Le `omp_get_wtick` fonction retourne une valeur à virgule flottante double précision égale au nombre de secondes entre les battements d’horloge successives. Le format est le suivant :

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
