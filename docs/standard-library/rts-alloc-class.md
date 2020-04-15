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
ms.openlocfilehash: 6ed84d906944a09fa355e281640e9480f3173554
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373423"
---
# <a name="rts_alloc-class"></a>rts_alloc, classe

Le modèle de classe rts_alloc décrit un [filtre](../standard-library/allocators-header.md) qui contient un éventail d’instances de cache et détermine l’instance à utiliser pour l’allocation et la transaction au moment de la transaction au lieu de le moment de la compilation.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Cache*|Type d'instances de cache contenu dans le tableau. Il peut s’agir de [cache_chunklist Class](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) ou [cache_suballoc](../standard-library/cache-suballoc-class.md).|

## <a name="remarks"></a>Notes

Ce modèle de classe contient plusieurs instances d’alloueur de bloc et détermine l’instance à utiliser pour l’allocation ou l’exécution au moment de l’exécution au lieu de le moment de compilation. Elle est utilisée avec les compilateurs qui ne peuvent pas compiler la reliaison.

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[Allouer](#allocate)|Alloue un bloc de mémoire.|
|[deallocate](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|
|[equals](#equals)|Compare l'égalité de deux caches.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="rts_allocallocate"></a><a name="allocate"></a>rts_alloc::allocate

Alloue un bloc de mémoire.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*count*|Nombre d’éléments du tableau à allouer.|

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’objet alloué.

### <a name="remarks"></a>Notes

La fonction `caches[_IDX].allocate(count)`membre retourne `_IDX` , lorsque l’indice est déterminé par le *nombre*de `operator new(count)`taille de bloc demandé, ou, si le *nombre* est trop grand, il retourne . `cache`, qui représente l’objet cache.

## <a name="rts_allocdeallocate"></a><a name="deallocate"></a>rts_alloc::dallocate

Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Ptr*|Pointeur vers le premier objet à désallouer dans le stockage.|
|*count*|Nombre d’objets à désallouer dans le stockage.|

### <a name="remarks"></a>Notes

La fonction `caches[_IDX].deallocate(ptr, count)`membre appelle `_IDX` , lorsque l’index est déterminé par le *nombre*de `operator delete(ptr)`taille de bloc demandé , ou, si le *nombre* est trop grand, il retourne .

## <a name="rts_allocequals"></a><a name="equals"></a>rts_alloc::égales

Compare l'égalité de deux caches.

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*_Cache*|Objet cache associé au filtre.|
|*_Other*|Objet cache dont l’égalité est à comparer.|

### <a name="remarks"></a>Notes

**vrai** si le `caches[0].equals(other.caches[0])`résultat de ; autrement, **faux**. `caches` représente le tableau d’objets cache.

## <a name="see-also"></a>Voir aussi

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<les allocataires>](../standard-library/allocators-header.md)
