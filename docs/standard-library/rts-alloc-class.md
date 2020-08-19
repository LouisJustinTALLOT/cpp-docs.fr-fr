---
title: rts_alloc, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
ms.openlocfilehash: 04a6578c7abd07ff84f4c0a5cee68cfd7ec8ef04
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560554"
---
# <a name="rts_alloc-class"></a>rts_alloc, classe

Le modèle de classe rts_alloc décrit un [filtre](../standard-library/allocators-header.md) qui contient un tableau d’instances de cache et détermine l’instance à utiliser pour l’allocation et la désallocation au moment de l’exécution plutôt qu’au moment de la compilation.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>Paramètres

*En*\
Type d'instances de cache contenu dans le tableau. Il peut s’agir [`cache_chunklist`](../standard-library/cache-chunklist-class.md) de, [`cache_freelist`](../standard-library/cache-freelist-class.md) ou [`cache_suballoc`](../standard-library/cache-suballoc-class.md) .

## <a name="remarks"></a>Notes

Ce modèle de classe contient plusieurs instances d’allocateur de bloc et détermine l’instance à utiliser pour l’allocation ou la désallocation au moment de l’exécution plutôt qu’au moment de la compilation. Elle est utilisée avec les compilateurs qui ne peuvent pas compiler la reliaison.

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[lui](#allocate)|Alloue un bloc de mémoire.|
|[libérer](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|
|[equals](#equals)|Compare l'égalité de deux caches.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<allocators>

**Espace de noms :** stdext

## <a name="rts_allocallocate"></a><a name="allocate"></a> rts_alloc :: Allocate

Alloue un bloc de mémoire.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Paramètres

*saut*\
Nombre d’éléments du tableau à allouer.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’objet alloué.

### <a name="remarks"></a>Notes

La fonction membre retourne `caches[_IDX].allocate(count)` , où l’index `_IDX` est déterminé par le *nombre*de tailles de bloc demandé, ou, si *Count* est trop grand, il retourne `operator new(count)` . `cache`, qui représente l’objet cache.

## <a name="rts_allocdeallocate"></a><a name="deallocate"></a> rts_alloc ::d eallocate

Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Paramètres

*effectués*\
Pointeur vers le premier objet à désallouer dans le stockage.

*saut*\
Nombre d’objets à désallouer dans le stockage.

### <a name="remarks"></a>Notes

La fonction membre appelle `caches[_IDX].deallocate(ptr, count)` , où l’index `_IDX` est déterminé par le *nombre*de tailles de bloc demandé, ou, si *Count* est trop grand, il retourne `operator delete(ptr)` .

## <a name="rts_allocequals"></a><a name="equals"></a> rts_alloc :: est égal à

Compare l'égalité de deux caches.

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>Paramètres

*_Cache*\
Objet cache associé au filtre.

*_Other*\
Objet cache dont l’égalité est à comparer.

### <a name="remarks"></a>Notes

**`true`** Si le résultat de `caches[0].equals(other.caches[0])` ; sinon, **`false`** . `caches` représente le tableau d’objets cache.

## <a name="see-also"></a>Voir aussi

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<allocators>](../standard-library/allocators-header.md)
