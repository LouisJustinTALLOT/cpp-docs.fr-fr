---
title: '&lt;allocators&gt;'
ms.date: 11/04/2016
f1_keywords:
- <allocators>
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
ms.openlocfilehash: f981b86ed8f5d3b240d9f02380a603eb4f2605bc
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623579"
---
# <a name="ltallocatorsgt"></a>&lt;allocators&gt;

Définit plusieurs modèles qui permettent d’allouer et de libérer des blocs de mémoire pour les conteneurs basés sur des nœuds.

## <a name="syntax"></a>Syntaxe

```cpp
#include <allocators>
```

> [!NOTE]
> \<allocators>est déconseillé, à compter de Visual Studio 2019 version 16,3.

## <a name="remarks"></a>Notes

L' \<allocators> en-tête fournit six modèles Allocator qui peuvent être utilisés pour sélectionner des stratégies de gestion de la mémoire pour les conteneurs basés sur des nœuds. En complément de ces modèles, il fournit également plusieurs filtres de synchronisation pour adapter la stratégie de gestion de mémoire à différents schémas de multithreading (y compris aucun). Vous pouvez accélérer votre application ou réduire ses besoins en mémoire en faisant correspondre une stratégie de gestion de la mémoire aux modèles d’utilisation de la mémoire et aux exigences de synchronisation.

Les modèles d’allocation sont implémentés avec des composants réutilisables qui peuvent être personnalisés ou remplacés pour fournir des stratégies de gestion de mémoire supplémentaires.

Les conteneurs basés sur des nœuds dans la bibliothèque standard C++ (std :: List, std :: Set, std :: multimultijeu, std :: Map et std :: Multimap) stockent leurs éléments dans des nœuds individuels. Tous les nœuds d’un type de conteneur particulier ont la même taille, il n’est donc pas nécessaire d’avoir recourt à la flexibilité d’un gestionnaire de mémoire à usage général. Comme la taille de chaque bloc de mémoire est connue au moment de la compilation, le gestionnaire de mémoire peut être beaucoup plus simple et plus rapide.

Lorsqu’ils sont utilisés avec des conteneurs qui ne sont pas basés sur des nœuds (tels que les conteneurs de bibliothèque standard C++ std :: Vector std ::d eque et std :: basic_string), les modèles allocateur fonctionnent correctement, mais ne peuvent pas améliorer les performances par rapport à l’allocateur par défaut.

Un Allocator est un modèle de classe qui décrit un objet qui gère l’allocation et la libération de stockage pour les objets et les tableaux d’objets d’un type désigné. Les objets allocateurs sont utilisés par plusieurs modèles de classe de conteneur dans la bibliothèque C++ standard.

Les allocateurs sont tous des modèles de ce type :

```cpp
template<class Type>
class allocator;
```

où l’argument de modèle `Type` est le type géré par l’instance d’allocateur. La bibliothèque C++ standard fournit un allocateur par défaut, [Allocator](allocator-class.md)de modèle de classe, qui est défini dans [\<memory>](memory.md) . L' \<allocators> en-tête fournit les allocateurs suivants :

- [allocator_newdel](allocator-newdel-class.md)

- [allocator_unbounded](allocator-unbounded-class.md)

- [allocator_fixed_size](allocator-fixed-size-class.md)

- [allocator_variable_size](allocator-variable-size-class.md)

- [allocator_suballoc](allocator-suballoc-class.md)

- [allocator_chunklist](allocator-chunklist-class.md)

Utilisez une instanciation d’allocateur appropriée comme deuxième argument de type quand vous créez un conteneur, comme dans l’exemple de code suivant.

```cpp
#include <list>
#include <allocators>
std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;
```

_List0 alloue des nœuds avec `allocator_chunklist` et le filtre de synchronisation par défaut.

Utilisez la macro [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) pour créer des modèles d’allocateur avec des filtres de synchronisation autre que celui par défaut :

```cpp
#include <list>
#include <allocators>
ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);
std::list<int, alloc<int> > _List1;
```

_Lst1 alloue des nœuds avec `allocator_chunklist` et le filtre de synchronisation [sync_per_thread](sync-per-thread-class.md).

Un allocateur de blocs est un cache ou un filtre. Un cache est un modèle de classe qui accepte un argument de type std :: size_t. Il définit un allocateur de blocs qui alloue et désalloue des blocs de mémoire de taille unique. Il doit obtenir de la mémoire à l’aide de l’opérateur **New**, mais il n’est pas nécessaire d’effectuer un appel distinct à Operator **New** pour chaque bloc. Il peut, par exemple, sous-allouer la mémoire d’un bloc plus grand ou mettre en cache des blocs désalloués en vue d’une réallocation ultérieure.

Avec un compilateur qui ne peut pas relier la valeur de l’argument std :: size_t utilisé lorsque le modèle a été instancié n’est pas nécessairement la valeur de l’argument _Sz passé aux fonctions membres Allocate et DEALLOCATE d’un cache.

\<allocators>fournit les modèles de cache suivants :

- [cache_freelist](cache-freelist-class.md)

- [cache_suballoc](cache-suballoc-class.md)

- [cache_chunklist](cache-chunklist-class.md)

Un filtre est un allocateur de bloc qui implémente ses fonctions membres à l’aide d’un autre allocateur de bloc, qui lui est passé comme argument de modèle. La forme de filtre la plus courante est le filtre de synchronisation, qui applique une stratégie de synchronisation pour contrôler l’accès aux fonctions membres d’une instance d’un autre allocateur de blocs. \<allocators>fournit les filtres de synchronisation suivants :

- [sync_none](sync-none-class.md)

- [sync_per_container](sync-per-container-class.md)

- [sync_per_thread](sync-per-thread-class.md)

- [sync_shared](sync-shared-class.md)

\<allocators>fournit également le filtre [rts_alloc](rts-alloc-class.md), qui contient plusieurs instances d’allocateur de bloc et détermine l’instance à utiliser pour l’allocation ou la désallocation au moment de l’exécution plutôt qu’au moment de la compilation. Elle est utilisée avec les compilateurs qui ne peuvent pas compiler la reliaison.

Une stratégie de synchronisation détermine comment une instance d’allocateur gère des demandes d’allocation et de désallocation simultanées à partir de plusieurs threads. La stratégie la plus simple consiste à passer toutes les demandes directement à l’objet cache sous-jacent, laissant à l’utilisateur la gestion de la synchronisation. Une stratégie plus complexe consiste à utiliser un mutex pour sérialiser l’accès à l’objet cache sous-jacent.

Si un compilateur prend en charge la compilation d’applications monothread et multithread, le filtre de synchronisation pour les applications monothread est `sync_none` ; et pour tous les autres cas `sync_shared`.

Le modèle de cache `cache_freelist` accepte un argument de classe Max, qui détermine le nombre maximal d’éléments à stocker dans la liste libre.

\<allocators>fournit les classes Max suivantes :

- [max_none](max-none-class.md)

- [max_unbounded](max-unbounded-class.md)

- [max_fixed_size](max-fixed-size-class.md)

- [max_variable_size](max-variable-size-class.md)

### <a name="macros"></a>Macros

|Macro|Description|
|-|-|
|[ALLOCATOR_DECL](allocators-functions.md#allocator_decl)|Produit un modèle de classe Allocator.|
|[CACHE_CHUNKLIST](allocators-functions.md#cache_chunklist)|Génère `stdext::allocators::cache_chunklist<sizeof(Type)>`.|
|[CACHE_FREELIST](allocators-functions.md#cache_freelist)|Génère `stdext::allocators::cache_freelist<sizeof(Type), max>`.|
|[CACHE_SUBALLOC](allocators-functions.md#cache_suballoc)|Génère `stdext::allocators::cache_suballoc<sizeof(Type)>`.|
|[SYNC_DEFAULT](allocators-functions.md#sync_default)|Génère un filtre de synchronisation.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur ! = ( \<allocators> )](allocators-operators.md#op_neq)|Vérifie l'inégalité entre les objets allocateurs d'une classe spécifiée.|
|[opérateur = = ( \<allocators> )](allocators-operators.md#op_eq_eq)|Vérifie l'égalité entre les objets allocateurs d'une classe spécifiée.|

### <a name="classes"></a>Classes

|Class|Description|
|-|-|
|[allocator_base](allocator-base-class.md)|Définit la classe de base et les fonctions communes nécessaires à la création d’un allocateur défini par l’utilisateur à partir d’un filtre de synchronisation.|
|[allocator_chunklist](allocator-chunklist-class.md)|Décrit un objet qui gère l’allocation et la libération de stockage pour des objets à l’aide d’un cache de type [cache_chunklist](cache-chunklist-class.md).|
|[allocator_fixed_size](allocator-fixed-size-class.md)|Décrit un objet qui gère l’allocation et la libération de stockage pour des objets de type `Type` à l’aide d’un cache de type [cache_freelist](cache-freelist-class.md) avec une longueur gérée par [max_fixed_size](max-fixed-size-class.md).|
|[allocator_newdel](allocator-newdel-class.md)|Implémente un allocateur qui utilise l' **opérateur delete** pour libérer un bloc de mémoire et un **nouvel opérateur** pour allouer un bloc de mémoire.|
|[allocator_suballoc](allocator-suballoc-class.md)|Décrit un objet qui gère l’allocation et la libération de stockage pour des objets de type `Type` à l’aide d’un cache de type [cache_suballoc](cache-suballoc-class.md).|
|[allocator_unbounded](allocator-unbounded-class.md)|Décrit un objet qui gère l’allocation et la libération de stockage pour des objets de type `Type` à l’aide d’un cache de type [cache_freelist](cache-freelist-class.md) avec une longueur gérée par [max_unbounded](max-unbounded-class.md).|
|[allocator_variable_size](allocator-variable-size-class.md)|Décrit un objet qui gère l’allocation et la libération de stockage pour des objets de type `Type` à l’aide d’un cache de type [cache_freelist](cache-freelist-class.md) avec une longueur gérée par [max_variable_size](max-variable-size-class.md).|
|[cache_chunklist](cache-chunklist-class.md)|Définit un allocateur de blocs qui alloue et désalloue des blocs de mémoire de taille unique.|
|[cache_freelist](cache-freelist-class.md)|Définit un allocateur de blocs qui alloue et désalloue des blocs de mémoire de taille unique.|
|[cache_suballoc](cache-suballoc-class.md)|Définit un allocateur de blocs qui alloue et désalloue des blocs de mémoire de taille unique.|
|[freelist](freelist-class.md)|Gère une liste de blocs de mémoire.|
|[max_fixed_size](max-fixed-size-class.md)|Décrit un objet de classe max qui limite un objet [freelist](freelist-class.md) à une longueur maximale fixe.|
|[max_none](max-none-class.md)|Décrit un objet de classe max qui limite un objet [freelist](freelist-class.md) à une longueur maximale de zéro.|
|[max_unbounded](max-unbounded-class.md)|Décrit un objet de classe max qui ne limite pas la longueur maximale d’un objet [freelist](freelist-class.md).|
|[max_variable_size](max-variable-size-class.md)|Décrit un objet de classe max qui limite un objet [freelist](freelist-class.md) à une longueur maximale qui est à peu près proportionnelle au nombre de blocs de mémoire alloués.|
|[rts_alloc](rts-alloc-class.md)|Le modèle de classe rts_alloc décrit un [filtre](allocators-header.md) qui contient un tableau d’instances de cache et détermine l’instance à utiliser pour l’allocation et la désallocation au moment de l’exécution plutôt qu’au moment de la compilation.|
|[sync_none](sync-none-class.md)|Décrit un filtre de synchronisation qui ne fournit aucune synchronisation.|
|[sync_per_container](sync-per-container-class.md)|Décrit un filtre de synchronisation qui fournit un objet de cache distinct pour chaque objet allocateur.|
|[sync_per_thread](sync-per-thread-class.md)|Décrit un filtre de synchronisation qui fournit un objet de cache distinct pour chaque thread.|
|[sync_shared](sync-shared-class.md)|Décrit un filtre de synchronisation qui utilise un mutex pour contrôler l’accès à un objet de cache partagé par tous les allocateurs.|

## <a name="requirements"></a>Configuration requise

**En-tête :**\<allocators>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](cpp-standard-library-header-files.md)
