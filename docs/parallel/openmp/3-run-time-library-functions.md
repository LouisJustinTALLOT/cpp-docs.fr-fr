---
title: 3. Fonctions de la bibliothèque du runtime
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 767c006b0a2d81af4d1f8f2e23f84d7847326f31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370271"
---
# <a name="3-run-time-library-functions"></a>3. Fonctions de bibliothèque de temps d’exécution

Cette section décrit les fonctions de bibliothèque OpenMP C et CMD. ** \<L’en-tête omp.h>** déclare deux types, plusieurs fonctions qui peuvent être utilisées pour contrôler et interroger l’environnement d’exécution parallèle, et verrouiller les fonctions qui peuvent être utilisées pour synchroniser l’accès aux données.

Le `omp_lock_t` type est un type d’objet capable de représenter qu’un verrou est disponible, ou qu’un thread possède un verrou. Ces serrures sont appelées *serrures simples.*

Le `omp_nest_lock_t` type est un type d’objet capable de représenter soit qu’une serrure est disponible, ou à la fois l’identité du fil qui possède la serrure et un *nombre de nidification* (décrit ci-dessous). Ces écluses sont appelées *écluses imbriquées.*

Les fonctions de bibliothèque sont des fonctions externes avec le lien « C ».

Les descriptions de ce chapitre sont divisées en sujets suivants :

- [Fonctions de l’environnement d’exécution](#31-execution-environment-functions)
- [Fonctions de verrouillage](#32-lock-functions)
- [Routines de synchronisation](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 Fonctions de l’environnement d’exécution

Les fonctions décrites dans cette section affectent et surveillent les fils, les processeurs et l’environnement parallèle :

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

### <a name="311-omp_set_num_threads-function"></a><a name="311-omp_set_num_threads-function"></a>3.1.1 fonction omp_set_num_threads

La `omp_set_num_threads` fonction définit le nombre par défaut de threads à `num_threads` utiliser pour les régions parallèles ultérieures qui ne spécifient pas une clause. au format suivant :

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

La valeur du paramètre *num_threads* doit être un integer positif. Son effet dépend de l’inseminage dynamique du nombre de threads activé. Pour un ensemble complet de règles `omp_set_num_threads` sur l’interaction entre la fonction et l’ajustement dynamique des threads, voir [l’article 2.3](2-directives.md#23-parallel-construct).

Cette fonction a les effets décrits ci-dessus `omp_in_parallel` lorsqu’ils sont appelés à partir d’une partie du programme où la fonction retourne zéro. Si cela s’appelle à partir d’une partie du programme où la `omp_in_parallel` fonction retourne une valeur non zéro, le comportement de cette fonction est indéfini.

Cet appel a préséance sur la variable de l’environnement. `OMP_NUM_THREADS` La valeur par défaut pour le nombre de `omp_set_num_threads` threads, `OMP_NUM_THREADS` qui peut être établi par appel `parallel` ou en définissant la variable de l’environnement, peut être explicitement remplacée sur une seule directive en spécifiant la `num_threads` clause.

Pour plus d’informations, voir [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Références croisées

- [fonction omp_set_dynamic](#317-omp_set_dynamic-function)
- [fonction omp_get_dynamic](#318-omp_get_dynamic-function)
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) variable de l’environnement
- [clause num_threads](2-directives.md#23-parallel-construct)

### <a name="312-omp_get_num_threads-function"></a><a name="312-omp_get_num_threads-function"></a>3.1.2 fonction omp_get_num_threads

La `omp_get_num_threads` fonction renvoie le nombre de threads actuellement dans l’équipe exécutant la région parallèle à partir de laquelle il est appelé. au format suivant :

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

La `num_threads` clause, `omp_set_num_threads` la fonction `OMP_NUM_THREADS` et la variable de l’environnement contrôlent le nombre de threads dans une équipe.

Si le nombre de threads n’a pas été explicitement défini par l’utilisateur, la valeur par défaut est définie par implémentation. Cette fonction se lie à `parallel` la directive d’enceinte la plus proche. Si appelé à partir d’une partie série d’un programme, ou d’une région parallèle imbriquée qui est sérialisée, cette fonction retourne 1.

Pour plus d’informations, voir [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Références croisées

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a><a name="313-omp_get_max_threads-function"></a>3.1.3 fonction omp_get_max_threads

La `omp_get_max_threads` fonction renvoie un intégrateur qui est garanti d’être au moins aussi grand que le nombre `num_threads` de threads qui seraient utilisés pour former une équipe si une région parallèle sans clause devait être vu à ce moment-là dans le code. au format suivant :

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

Ce qui suit exprime une `omp_get_max_threads`limite inférieure sur la valeur de :

> *threads-used-for-next-team* <= `omp_get_max_threads`

Notez que si une `num_threads` autre région parallèle utilise la clause pour demander un nombre `omp_get_max_threads` spécifique de threads, la garantie sur la limite inférieure du résultat de ne plus tenir.

La `omp_get_max_threads` valeur de retour de la fonction peut être utilisée pour allouer dynamiquement un stockage suffisant pour tous les threads de l’équipe formée dans la région parallèle suivante.

#### <a name="cross-references"></a>Références croisées

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a><a name="314-omp_get_thread_num-function"></a>3.1.4 fonction omp_get_thread_num

La `omp_get_thread_num` fonction renvoie le numéro de thread, au sein de son équipe, du thread exécutant la fonction. Le numéro de fil `omp_get_num_threads()`se situe entre 0 et -1, inclusivement. Le fil de maître de l’équipe est le fil 0.

au format suivant :

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

S’il est appelé `omp_get_thread_num` d’une région en série, retourne 0. Si appelé de l’intérieur d’une région parallèle imbriquée qui est sérialisée, cette fonction revient 0.

#### <a name="cross-references"></a>Références croisées

- [fonction omp_get_num_threads](#312-omp_get_num_threads-function)

### <a name="315-omp_get_num_procs-function"></a><a name="315-omp_get_num_procs-function"></a>3.1.5 fonction omp_get_num_procs

La `omp_get_num_procs` fonction renvoie le nombre de processeurs qui sont disponibles pour le programme au moment où la fonction est appelée. au format suivant :

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a><a name="316-omp_in_parallel-function"></a>3.1.6 fonction omp_in_parallel

La `omp_in_parallel` fonction retourne une valeur non zéro si elle est appelée dans l’étendue dynamique d’une région parallèle exécutant en parallèle; sinon, il revient 0. au format suivant :

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

Cette fonction retourne une valeur non zéro lorsqu’elle est appelée de l’intérieur d’une région exécutant en parallèle, y compris les régions imbriquées qui sont sérialisées.

### <a name="317-omp_set_dynamic-function"></a><a name="317-omp_set_dynamic-function"></a>3.1.7 fonction omp_set_dynamic

La `omp_set_dynamic` fonction permet ou désactive l’ajustement dynamique du nombre de threads disponibles pour l’exécution des régions parallèles. au format suivant :

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Si *dynamic_threads* évalue à une valeur non zéro, le nombre de threads utilisés pour l’exécution des régions parallèles à venir peut être ajusté automatiquement par l’environnement de temps d’exécution pour utiliser au mieux les ressources du système. En conséquence, le nombre de threads spécifiés par l’utilisateur est le nombre maximum de threads. Le nombre de threads dans l’équipe exécutant une région parallèle reste fixe `omp_get_num_threads` pour la durée de cette région parallèle et est signalé par la fonction.

Si *dynamic_threads* évalue à 0, l’ajustement dynamique est désactivé.

Cette fonction a les effets décrits ci-dessus `omp_in_parallel` lorsqu’ils sont appelés à partir d’une partie du programme où la fonction retourne zéro. Si cela s’appelle à partir d’une partie du programme où la `omp_in_parallel` fonction retourne une valeur non zéro, le comportement de cette fonction est indéfini.

Un appel `omp_set_dynamic` à la `OMP_DYNAMIC` préséance sur la variable de l’environnement.

La valeur par défaut pour l’ajustement dynamique des threads est définie par implémentation. En conséquence, les codes d’utilisateur qui dépendent d’un nombre spécifique de threads pour une exécution correcte devraient explicitement désactiver les threads dynamiques. Les implémentations ne sont pas nécessaires pour fournir la possibilité d’ajuster dynamiquement le nombre de threads, mais elles sont nécessaires pour fournir l’interface pour prendre en charge la portabilité sur toutes les plates-formes.

#### <a name="microsoft-specific"></a>Spécifique à Microsoft

Le soutien `omp_get_dynamic` actuel `omp_set_dynamic` de et est le suivant:

Le paramètre `omp_set_dynamic` d’entrée n’affecte pas la stratégie de threading et ne modifie pas le nombre de threads. `omp_get_num_threads`renvoie toujours soit le numéro défini par l’utilisateur, si tel est défini, soit le numéro de thread par défaut. Dans la mise `omp_set_dynamic(0)` en œuvre actuelle de Microsoft, éteint le threading dynamique de sorte que l’ensemble existant de threads peut être réutilisé pour la région parallèle suivante. `omp_set_dynamic(1)`active le threading dynamique en rejetant l’ensemble existant de threads et en créant un nouvel ensemble pour la région parallèle à venir. Le nombre de threads dans le nouvel ensemble est le même que `omp_get_num_threads`l’ancien ensemble, et est basé sur la valeur de retour de . Par conséquent, pour `omp_set_dynamic(0)` les meilleures performances, utilisez-le pour réutiliser les threads existants.

#### <a name="cross-references"></a>Références croisées

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a><a name="318-omp_get_dynamic-function"></a>3.1.8 fonction omp_get_dynamic

La `omp_get_dynamic` fonction retourne une valeur non zéro si l’ajustement dynamique des threads est activé, et retourne 0 autrement. au format suivant :

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

Si la implémentation ne met pas en œuvre un ajustement dynamique du nombre de threads, cette fonction renvoie toujours 0. Pour plus d’informations, voir [omp_set_dynamic](#317-omp_set_dynamic-function).

#### <a name="cross-references"></a>Références croisées

- Pour une description de l’ajustement dynamique du thread, voir [omp_set_dynamic](#317-omp_set_dynamic-function).

### <a name="319-omp_set_nested-function"></a><a name="319-omp_set_nested-function"></a>3.1.9 fonction omp_set_nested

La `omp_set_nested` fonction permet ou désactive le parallélisme imbriqué. au format suivant :

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

Si les évaluations *imbriquées* sont 0, le parallélisme imbriqué est désactivé, ce qui est par défaut, et les régions parallèles imbriquées sont sérialisées et exécutées par le fil actuel. Dans le cas contraire, le parallélisme imbriqué est activé, et les régions parallèles qui sont imbriquées peuvent déployer des fils supplémentaires pour former des équipes imbriquées.

Cette fonction a les effets décrits ci-dessus `omp_in_parallel` lorsqu’ils sont appelés à partir d’une partie du programme où la fonction retourne zéro. Si cela s’appelle à partir d’une partie du programme où la `omp_in_parallel` fonction retourne une valeur non zéro, le comportement de cette fonction est indéfini.

Cet appel a préséance sur la variable de l’environnement. `OMP_NESTED`

Lorsque le parallélisme imbriqué est activé, le nombre de fils utilisés pour exécuter les régions parallèles imbriquées est défini par implémentation. En conséquence, les implémentations conformes à OpenMP sont autorisées à sérialiser les régions parallèles imbriquées même lorsque le parallélisme imbriqué est activé.

#### <a name="cross-references"></a>Références croisées

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a><a name="3110-omp_get_nested-function"></a>3.1.10 fonction omp_get_nested

La `omp_get_nested` fonction retourne une valeur non zéro si le parallélisme imbriqué est activé et 0 si elle est désactivée. Pour plus d’informations sur le parallélisme imbriqué, voir [omp_set_nested](#319-omp_set_nested-function). au format suivant :

```cpp
#include <omp.h>
int omp_get_nested(void);
```

Si une implémentation ne met pas en œuvre le parallélisme imbriqué, cette fonction revient toujours 0.

## <a name="32-lock-functions"></a>3.2 Fonctions de verrouillage

Les fonctions décrites dans cette section manipulent les serrures utilisées pour la synchronisation.

Pour les fonctions suivantes, la `omp_lock_t`variable de verrouillage doit avoir le type . Cette variable ne doit être accessible que par ces fonctions. Toutes les fonctions de verrouillage exigent `omp_lock_t` un argument qui a un pointeur à taper.

- La fonction [omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) est parasorisée d’un verrou simple.
- La fonction [omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) supprime un verrou simple.
- La fonction [omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) attend qu’un verrou simple soit disponible.
- La fonction [omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) libère un verrou simple.
- La fonction [omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) teste un verrou simple.

Pour les fonctions suivantes, la `omp_nest_lock_t`variable de verrouillage doit avoir le type .  Cette variable ne doit être accessible que par ces fonctions. Toutes les fonctions de verrouillage imbriquées exigent un argument qui a un pointeur à `omp_nest_lock_t` taper.

- La fonction [omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions) est parassible une écluse nichable.
- La fonction [omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) enlève une serrure oisissable.
- La fonction [omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions) attend qu’une serrure imbriquée soit disponible.
- La fonction [omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions) libère une serrure imbriquée.
- La fonction [omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions) teste une serrure imbriquée.

Les fonctions de verrouillage OpenMP accèdent à la variable de verrouillage de telle sorte qu’elles lisent et mettent à jour la valeur la plus actuelle de la variable de verrouillage. Par conséquent, il n’est pas nécessaire `flush` pour un programme OpenMP d’inclure des directives explicites pour s’assurer que la valeur de la variable de verrouillage est cohérente entre les différents threads. (Il peut être `flush` nécessaire de directives pour rendre les valeurs d’autres variables cohérentes.)

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a><a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a>3.2.1 fonctions omp_init_lock et omp_init_nest_lock

Ces fonctions fournissent le seul moyen d’initialiser un verrou. Chaque fonction initialise le verrou associé au *verrou* de paramètres pour une utilisation dans les appels à venir. au format suivant :

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

L’état initial est déverrouillé (c’est-à-dire qu’aucun thread n’est propriétaire de la serrure). Pour une écluse imbriquée, le nombre initial de nidification est nul. Il n’est pas conforme d’appeler l’une ou l’autre de ces routines avec une variable de verrouillage qui a déjà été initialisé.

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a><a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a>3.2.2 fonctions omp_destroy_lock et omp_destroy_nest_lock

Ces fonctions s’assurent que le *verrou* variable de verrouillage pointu est uninitialisé. au format suivant :

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

Il n’est pas conforme d’appeler l’une ou l’autre de ces routines avec une variable de verrouillage qui est uninitialisé ou déverrouillé.

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a><a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a>3.2.3 fonctions omp_set_lock et omp_set_nest_lock

Chacune de ces fonctions bloque le thread exécutant la fonction jusqu’à ce que le verrou spécifié soit disponible, puis définit le verrou. Un verrou simple est disponible s’il est déverrouillé. Une serrure nestable est disponible si elle est déverrouillée ou si elle est déjà détenue par le fil exécutant la fonction. au format suivant :

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Pour un verrou simple, `omp_set_lock` l’argument de la fonction doit indiquer une variable de verrouillage initialisée. La propriété du verrou est accordée au thread exécutant la fonction.

Pour une serrure imbriquée, l’argument de la `omp_set_nest_lock` fonction doit indiquer une variable de verrouillage initialisée. Le nombre de nidifications est incrémenté, et le fil est accordé, ou conserve, la propriété de la serrure.

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a><a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a>3.2.4 fonctions omp_unset_lock et omp_unset_nest_lock

Ces fonctions fournissent les moyens de libérer la propriété d’un verrou. au format suivant :

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

L’argument de chacune de ces fonctions doit indiquer une variable de verrouillage initialisée appartenant au fil exécutant la fonction. Le comportement n’est pas défini si le fil ne possède pas ce verrou.

Pour un verrou `omp_unset_lock` simple, la fonction libère le thread exécutant la fonction de propriété du verrou.

Pour une serrure imbriquée, la `omp_unset_nest_lock` fonction décrète le nombre de nidifications et libère le fil exécutant la fonction de propriété de la serrure si le nombre résultant est nul.

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a><a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a>3.2.5 fonctions omp_test_lock et omp_test_nest_lock

Ces fonctions tentent de régler un verrou, mais ne bloquent pas l’exécution du fil. au format suivant :

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

L’argument doit indiquer une variable de verrouillage initialisée. Ces fonctions tentent de définir un `omp_set_lock` verrou `omp_set_nest_lock`de la même manière que et , sauf qu’ils ne bloquent pas l’exécution du fil.

Pour un verrou `omp_test_lock` simple, la fonction renvoie une valeur non zéro si le verrou est réglé avec succès; sinon, il retourne zéro.

Pour une serrure imbriquée, la `omp_test_nest_lock` fonction renvoie le nouveau nombre de nidifications si l’écluse est réglée avec succès; sinon, il retourne zéro.

## <a name="33-timing-routines"></a>3.3 Routines de chronométrage

Les fonctions décrites dans cette section prennent en charge une minuterie portative d’horloge murale :

- La fonction [omp_get_wtime](#331-omp_get_wtime-function) renvoie l’heure de l’horloge murale.
- La fonction [omp_get_wtick](#332-omp_get_wtick-function) renvoie des secondes entre les tiques successives de l’horloge.

### <a name="331-omp_get_wtime-function"></a><a name="331-omp_get_wtime-function"></a>3.3.1 fonction omp_get_wtime

La `omp_get_wtime` fonction renvoie une valeur de point flottant de double précision égale au temps d’horloge mural écoulé en quelques secondes depuis un certain "temps dans le passé".  Le « temps dans le passé » est arbitraire, mais il est garanti de ne pas changer pendant l’exécution du programme d’application. au format suivant :

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

On s’attend à ce que la fonction soit utilisée pour mesurer les temps écoulés comme le montre l’exemple suivant :

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Les temps retournés sont des « temps par thread » par lesquels ils ne sont pas tenus d’être globalement cohérents sur tous les threads participant à une application.

### <a name="332-omp_get_wtick-function"></a><a name="332-omp_get_wtick-function"></a>3.3.2 fonction omp_get_wtick

La `omp_get_wtick` fonction renvoie une valeur de point flottant de double précision égale au nombre de secondes entre les tiques successives d’horloge. au format suivant :

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
