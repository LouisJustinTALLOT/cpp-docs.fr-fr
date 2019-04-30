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
ms.openlocfilehash: 3cb1946ee68642065488cfd13c146abab818ec60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412317"
---
# <a name="syncperthread-class"></a>sync_per_thread, classe

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

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[allocate](#allocate)|Alloue un bloc de mémoire.|
|[deallocate](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|
|[equals](#equals)|Compare l'égalité de deux caches.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="allocate"></a>  sync_per_thread::allocate

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

## <a name="deallocate"></a>  sync_per_thread::deallocate

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

La fonction membre appelle `deallocate` sur l’objet cache appartenant au thread actuel. Si aucun objet cache n’a été alloué pour le thread actuel, elle commence par en allouer un.

## <a name="equals"></a>  sync_per_thread::equals

Compare l'égalité de deux caches.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Cache*|L’objet cache du filtre de synchronisation.|
|*Autre*|Objet cache dont l’égalité est à comparer.|

### <a name="return-value"></a>Valeur de retour

**false** si aucun objet cache a été alloué pour cet objet ou pour *autres* dans le thread actuel. Sinon, elle retourne le résultat de l’application de `operator==` aux deux objets caches.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)<br/>
