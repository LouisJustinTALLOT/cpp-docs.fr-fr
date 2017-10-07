---
title: '&lt;allocators&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <allocators>
dev_langs:
- C++
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: cf6f722eaa4f71a808ec416aa7646c7fe4de2689
ms.contentlocale: fr-fr
ms.lasthandoff: 10/03/2017

---
# <a name="ltallocatorsgt"></a>&lt;allocators&gt;
Définit plusieurs modèles qui permettent d’allouer et de libérer des blocs de mémoire pour les conteneurs basés sur des nœuds.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <allocators>  
```  
  
## <a name="remarks"></a>Notes  
 L’en-tête \<allocators> fournit six modèles d’allocation qui peuvent être utilisés pour sélectionner des stratégies de gestion de mémoire pour les conteneurs basés sur des nœuds. En complément de ces modèles, il fournit également plusieurs filtres de synchronisation pour adapter la stratégie de gestion de mémoire à différents schémas de multithreading (y compris aucun). Quand vous adaptez une stratégie de gestion de mémoire aux modèles d’utilisation de mémoire connus et aux exigences de synchronisation d’une application particulière, vous pouvez souvent augmenter la vitesse de cette application ou réduire ses besoins en mémoire globale.  
  
 Les modèles d’allocation sont implémentés avec des composants réutilisables qui peuvent être personnalisés ou remplacés pour fournir des stratégies de gestion de mémoire supplémentaires.  
  
 Les conteneurs basés sur des nœuds dans la bibliothèque C++ Standard (std::list, std::set, std::multiset, std::map et std::multimap) stockent leurs éléments dans des nœuds individuels. Tous les nœuds d’un type de conteneur particulier ont la même taille, il n’est donc pas nécessaire d’avoir recourt à la flexibilité d’un gestionnaire de mémoire à usage général. Comme la taille de chaque bloc de mémoire est connue au moment de la compilation, le gestionnaire de mémoire peut être beaucoup plus simple et plus rapide.  
  
 Quand ils sont utilisés avec des conteneurs qui ne sont pas basés sur des nœuds (par exemple, les conteneurs de bibliothèque C++ Standard std::vector, std::deque et std::basic_string), les modèles d’allocation fonctionnent correctement, mais n’améliorent pas forcément les performances par rapport à l’allocateur par défaut.  
  
 Un allocateur est une classe de modèle qui décrit un objet gérant l’allocation et la libération de stockage pour des objets et des tableaux d’objets d’un type désigné. Les objets allocateur sont utilisés par plusieurs classes de modèle de conteneur dans la bibliothèque C++ Standard.  
  
 Les allocateurs sont tous des modèles de ce type :  
  
 `template<class` `Type` `>`  
  
 `class allocator;`  
  
 où l’argument de modèle `Type` est le type géré par l’instance d’allocateur. La bibliothèque C++ Standard fournit un allocateur par défaut, la classe de modèle [allocator](../standard-library/allocator-class.md), définie dans [\<memory>](../standard-library/memory.md). L’en-tête \<allocators> fournit les allocateurs suivants :  
  
- [allocator_newdel](../standard-library/allocator-newdel-class.md)  
  
- [allocator_unbounded](../standard-library/allocator-unbounded-class.md)  
  
- [allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)  
  
- [allocator_variable_size](../standard-library/allocator-variable-size-class.md)  
  
- [allocator_suballoc](../standard-library/allocator-suballoc-class.md)  
  
- [allocator_chunklist](../standard-library/allocator-chunklist-class.md)  
  
 Utilisez une instanciation d’allocateur appropriée comme deuxième argument de type quand vous créez un conteneur, comme dans l’exemple de code suivant.  
  
 `#include <list>`  
  
 `#include <allocators>`  
  
 `std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;`  
  
 _List0 alloue des nœuds avec `allocator_chunklist` et le filtre de synchronisation par défaut.  
  
 Utilisez la macro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) pour créer des modèles d’allocateur avec des filtres de synchronisation autre que celui par défaut :  
  
 `#include <list>`  
  
 `#include <allocators>`  
  
 `ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);`  
  
 `std::list<int, alloc<int> > _List1;`  
  
 _Lst1 alloue des nœuds avec `allocator_chunklist` et le filtre de synchronisation [sync_per_thread](../standard-library/sync-per-thread-class.md).  
  
 Un allocateur de blocs est un cache ou un filtre. Un cache est une classe de modèle qui accepte un argument de type std::size_t. Il définit un allocateur de blocs qui alloue et désalloue des blocs de mémoire de taille unique. Il doit obtenir de la mémoire à l’aide de l’opérateur `new`, mais il n’a pas besoin d’effectuer un appel distinct à l’opérateur `new` pour chaque bloc. Il peut, par exemple, sous-allouer la mémoire d’un bloc plus grand ou mettre en cache des blocs désalloués en vue d’une réallocation ultérieure.  
  
 Avec un compilateur qui ne peut pas compiler rebind, la valeur de l’argument std::size_t utilisé quand le modèle a été instancié n’est pas nécessairement la valeur de l’argument _Sz passé aux fonctions membres allocate et deallocate d’un cache.  
  
 \<allocators> fournit les modèles de cache suivants :  
  
- [cache_freelist](../standard-library/cache-freelist-class.md)  
  
- [cache_suballoc](../standard-library/cache-suballoc-class.md)  
  
- [cache_chunklist](../standard-library/cache-chunklist-class.md)  
  
 Un filtre est un allocateur de blocs qui implémente ses fonctions membres à l’aide d’un autre allocateur de blocs transmis comme un argument de modèle. La forme de filtre la plus courante est le filtre de synchronisation, qui applique une stratégie de synchronisation pour contrôler l’accès aux fonctions membres d’une instance d’un autre allocateur de blocs. \<allocators> fournit les filtres de synchronisation suivants :  
  
- [sync_none](../standard-library/sync-none-class.md)  
  
- [sync_per_container](../standard-library/sync-per-container-class.md)  
  
- [sync_per_thread](../standard-library/sync-per-thread-class.md)  
  
- [sync_shared](../standard-library/sync-shared-class.md)  
  
 \<allocators> fournit également le filtre [rts_alloc](../standard-library/rts-alloc-class.md), qui contient plusieurs instances d’allocateur de blocs, et détermine l’instance à utiliser pour l’allocation ou la désallocation au moment de l’exécution plutôt qu’au moment de la compilation. Elle est utilisée avec les compilateurs qui ne peuvent pas compiler la reliaison.  
  
 Une stratégie de synchronisation détermine comment une instance d’allocateur gère des demandes d’allocation et de désallocation simultanées à partir de plusieurs threads. La stratégie la plus simple consiste à passer toutes les demandes directement à l’objet cache sous-jacent, laissant à l’utilisateur la gestion de la synchronisation. Une stratégie plus complexe consiste à utiliser un mutex pour sérialiser l’accès à l’objet cache sous-jacent.  
  
 Si un compilateur prend en charge la compilation d’applications monothread et multithread, le filtre de synchronisation pour les applications monothread est `sync_none` ; et pour tous les autres cas `sync_shared`.  
  
 Le modèle de cache `cache_freelist` accepte un argument de classe max qui détermine le nombre maximal d’éléments à stocker dans la liste de libération.  
  
 \<allocators> fournit les classes max suivantes :  
  
- [max_none](../standard-library/max-none-class.md)  
  
- [max_unbounded](../standard-library/max-unbounded-class.md)  
  
- [max_fixed_size](../standard-library/max-fixed-size-class.md)  
  
- [max_variable_size](../standard-library/max-variable-size-class.md)  
  
### <a name="macros"></a>Macros  
  
|||  
|-|-|  
|[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)|Génère une classe de modèle allocator.|  
|[CACHE_CHUNKLIST](../standard-library/allocators-functions.md#cache_chunklist)|Génère `stdext::allocators::cache_chunklist<sizeof(Type)>`.|  
|[CACHE_FREELIST](../standard-library/allocators-functions.md#cache_freelist)|Génère `stdext::allocators::cache_freelist<sizeof(Type), max>`.|  
|[CACHE_SUBALLOC](../standard-library/allocators-functions.md#cache_suballoc)|Génère `stdext::allocators::cache_suballoc<sizeof(Type)>`.|  
|[SYNC_DEFAULT](../standard-library/allocators-functions.md#sync_default)|Génère un filtre de synchronisation.|  
  
### <a name="operators"></a>Opérateurs  
  
|||  
|-|-|  
|[operator!= (\<allocators>)](../standard-library/allocators-operators.md#op_neq)|Vérifie l'inégalité entre les objets allocateurs d'une classe spécifiée.|  
|[operator== (\<allocators>)](../standard-library/allocators-operators.md#op_eq_eq)|Vérifie l'égalité entre les objets allocateurs d'une classe spécifiée.|  
  
### <a name="classes"></a>Classes  
  
|||  
|-|-|  
|[allocator_base](../standard-library/allocator-base-class.md)|Définit la classe de base et les fonctions communes nécessaires à la création d’un allocateur défini par l’utilisateur à partir d’un filtre de synchronisation.|  
|[allocator_chunklist](../standard-library/allocator-chunklist-class.md)|Décrit un objet qui gère l’allocation et la libération de stockage pour des objets à l’aide d’un cache de type [cache_chunklist](../standard-library/cache-chunklist-class.md).|  
|[allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)|Décrit un objet qui gère l’allocation et la libération de stockage pour des objets de type `Type` à l’aide d’un cache de type [cache_freelist](../standard-library/cache-freelist-class.md) avec une longueur gérée par [max_fixed_size](../standard-library/max-fixed-size-class.md).|  
|[allocator_newdel](../standard-library/allocator-newdel-class.md)|Implémente un allocateur qui utilise `operator delete` pour désallouer un bloc de mémoire et `operator new` pour allouer un bloc de mémoire.|  
|[allocator_suballoc](../standard-library/allocator-suballoc-class.md)|Décrit un objet qui gère l’allocation et la libération de stockage pour des objets de type `Type` à l’aide d’un cache de type [cache_suballoc](../standard-library/cache-suballoc-class.md).|  
|[allocator_unbounded](../standard-library/allocator-unbounded-class.md)|Décrit un objet qui gère l’allocation et la libération de stockage pour des objets de type `Type` à l’aide d’un cache de type [cache_freelist](../standard-library/cache-freelist-class.md) avec une longueur gérée par [max_unbounded](../standard-library/max-unbounded-class.md).|  
|[allocator_variable_size](../standard-library/allocator-variable-size-class.md)|Décrit un objet qui gère l’allocation et la libération de stockage pour des objets de type `Type` à l’aide d’un cache de type [cache_freelist](../standard-library/cache-freelist-class.md) avec une longueur gérée par [max_variable_size](../standard-library/max-variable-size-class.md).|  
|[cache_chunklist](../standard-library/cache-chunklist-class.md)|Définit un allocateur de blocs qui alloue et désalloue des blocs de mémoire de taille unique.|  
|[cache_freelist](../standard-library/cache-freelist-class.md)|Définit un allocateur de blocs qui alloue et désalloue des blocs de mémoire de taille unique.|  
|[cache_suballoc](../standard-library/cache-suballoc-class.md)|Définit un allocateur de blocs qui alloue et désalloue des blocs de mémoire de taille unique.|  
|[freelist](../standard-library/freelist-class.md)|Gère une liste de blocs de mémoire.|  
|[max_fixed_size](../standard-library/max-fixed-size-class.md)|Décrit un objet de classe max qui limite un objet [freelist](../standard-library/freelist-class.md) à une longueur maximale fixe.|  
|[max_none](../standard-library/max-none-class.md)|Décrit un objet de classe max qui limite un objet [freelist](../standard-library/freelist-class.md) à une longueur maximale de zéro.|  
|[max_unbounded](../standard-library/max-unbounded-class.md)|Décrit un objet de classe max qui ne limite pas la longueur maximale d’un objet [freelist](../standard-library/freelist-class.md).|  
|[max_variable_size](../standard-library/max-variable-size-class.md)|Décrit un objet de classe max qui limite un objet [freelist](../standard-library/freelist-class.md) à une longueur maximale qui est à peu près proportionnelle au nombre de blocs de mémoire alloués.|  
|[rts_alloc](../standard-library/rts-alloc-class.md)|La classe de modèle rts_alloc décrit un [filtre](../standard-library/allocators-header.md) qui contient un tableau d’instances de cache et détermine l’instance à utiliser pour l’allocation et la désallocation au moment de l’exécution plutôt qu’au moment de la compilation.|  
|[sync_none](../standard-library/sync-none-class.md)|Décrit un filtre de synchronisation qui ne fournit aucune synchronisation.|  
|[sync_per_container](../standard-library/sync-per-container-class.md)|Décrit un filtre de synchronisation qui fournit un objet de cache distinct pour chaque objet allocateur.|  
|[sync_per_thread](../standard-library/sync-per-thread-class.md)|Décrit un filtre de synchronisation qui fournit un objet de cache distinct pour chaque thread.|  
|[sync_shared](../standard-library/sync-shared-class.md)|Décrit un filtre de synchronisation qui utilise un mutex pour contrôler l’accès à un objet de cache partagé par tous les allocateurs.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<allocators>  
  
 **Espace de noms :** stdext  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)




