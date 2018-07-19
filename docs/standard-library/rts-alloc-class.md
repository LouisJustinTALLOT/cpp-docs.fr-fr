---
title: rts_alloc, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4bff519ea12646e94e92cde219fa38e4009a767
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956452"
---
# <a name="rtsalloc-class"></a>rts_alloc, classe

La classe de modèle rts_alloc décrit un [filtre](../standard-library/allocators-header.md) qui contient un tableau d’instances de cache et détermine l’instance à utiliser pour l’allocation et la libération au moment de l’exécution plutôt qu’au moment de la compilation.

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

Cette classe de modèle contient plusieurs instances d'allocateur de bloc et détermine quelle instance utiliser pour l'allocation ou la désallocation au moment de l'exécution plutôt qu'au moment de la compilation. Elle est utilisée avec les compilateurs qui ne peuvent pas compiler la reliaison.

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[allocate](#allocate)|Alloue un bloc de mémoire.|
|[deallocate](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|
|[equals](#equals)|Compare l'égalité de deux caches.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="allocate"></a>  rts_alloc::allocate

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

La fonction membre retourne `caches[_IDX].allocate(count)`, où l’index `_IDX` est déterminée par la taille de bloc demandé *nombre*, ou, si *nombre* est trop volumineux, il retourne `operator new(count)`. `cache`, qui représente l’objet cache.

## <a name="deallocate"></a>  rts_alloc::deallocate

Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*ptr*|Pointeur vers le premier objet à désallouer dans le stockage.|
|*count*|Nombre d’objets à désallouer dans le stockage.|

### <a name="remarks"></a>Notes

La fonction membre appelle `caches[_IDX].deallocate(ptr, count)`, où l’index `_IDX` est déterminée par la taille de bloc demandé *nombre*, ou, si *nombre* est trop volumineux, il retourne `operator delete(ptr)`.

## <a name="equals"></a>  rts_alloc::equals

Compare l'égalité de deux caches.

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*_Cache*|Objet cache associé au filtre.|
|*_Autre*|Objet cache dont l’égalité est à comparer.|

### <a name="remarks"></a>Notes

**true** si le résultat de `caches[0].equals(other.caches[0])`; sinon, **false**. `caches` représente le tableau d’objets cache.

## <a name="see-also"></a>Voir aussi

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)<br/>
[\<allocators>](../standard-library/allocators-header.md)<br/>
