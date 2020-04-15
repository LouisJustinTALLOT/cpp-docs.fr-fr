---
title: sync_per_thread, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_thread
- allocators/stdext::sync_per_thread::allocate
- allocators/stdext::sync_per_thread::deallocate
- allocators/stdext::sync_per_thread::equals
helpviewer_keywords:
- stdext::sync_per_thread
- stdext::sync_per_thread [C++], allocate
- stdext::sync_per_thread [C++], deallocate
- stdext::sync_per_thread [C++], equals
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
ms.openlocfilehash: 2976cdc6671750f0da439e9eb42053518e4af8d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376546"
---
# <a name="sync_per_thread-class"></a>sync_per_thread, classe

Décrit un [filtre de synchronisation](../standard-library/allocators-header.md) qui fournit un objet cache distinct pour chaque thread.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_per_thread
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Cache*|Type de cache associé au filtre de synchronisation. Il peut s’agir de [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) ou [cache_suballoc](../standard-library/cache-suballoc-class.md).|

## <a name="remarks"></a>Notes

Les allocateurs qui utilisent `sync_per_thread` peuvent être considérés comme égaux même si des blocs alloués dans un thread ne peuvent pas être désalloués à partir d’un autre thread. Quand un de ces allocateurs est utilisé, les blocs de mémoire alloués dans un thread ne doivent pas être visibles pour d’autres threads. Dans la pratique, cela signifie qu’un conteneur qui utilise un de ces allocateurs doit uniquement être accessible par un seul thread.

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[Allouer](#allocate)|Alloue un bloc de mémoire.|
|[deallocate](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|
|[equals](#equals)|Compare l'égalité de deux caches.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="sync_per_threadallocate"></a><a name="allocate"></a>sync_per_thread::allocate

Alloue un bloc de mémoire.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*count*|Nombre d’éléments du tableau à allouer.|

### <a name="remarks"></a>Notes

La fonction membre retourne le résultat d’un appel à `cache::allocate(count)` sur l’objet cache appartenant au thread actuel. Si aucun objet cache n’a été alloué pour le thread actuel, elle commence par en allouer un.

## <a name="sync_per_threaddeallocate"></a><a name="deallocate"></a>sync_per_thread::dallocate

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

La fonction membre appelle `deallocate` sur l’objet cache appartenant au thread actuel. Si aucun objet cache n’a été alloué pour le thread actuel, elle commence par en allouer un.

## <a name="sync_per_threadequals"></a><a name="equals"></a>sync_per_thread::égales

Compare l'égalité de deux caches.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Cache*|L’objet cache du filtre de synchronisation.|
|*Autres*|Objet cache dont l’égalité est à comparer.|

### <a name="return-value"></a>Valeur de retour

**faux** si aucun objet de cache n’a été attribué pour cet objet ou pour *Autre* dans le thread actuel. Sinon, elle retourne le résultat de l’application de `operator==` aux deux objets caches.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[\<les allocataires>](../standard-library/allocators-header.md)
