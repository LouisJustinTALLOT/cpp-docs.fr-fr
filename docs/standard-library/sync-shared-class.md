---
title: sync_shared, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_shared
- allocators/stdext::sync_shared::allocate
- allocators/stdext::sync_shared::deallocate
- allocators/stdext::sync_shared::equals
helpviewer_keywords:
- stdext::sync_shared
- stdext::sync_shared [C++], allocate
- stdext::sync_shared [C++], deallocate
- stdext::sync_shared [C++], equals
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
ms.openlocfilehash: 029edea59f29534491232d5d99353ccb093447bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376535"
---
# <a name="sync_shared-class"></a>sync_shared, classe

Décrit un [filtre de synchronisation](../standard-library/allocators-header.md) qui utilise un mutex pour contrôler l’accès à un objet cache partagé par tous les allocateurs.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_shared
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Cache*|Type de cache associé au filtre de synchronisation. Il peut s’agir de [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) ou [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[Allouer](#allocate)|Alloue un bloc de mémoire.|
|[deallocate](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|
|[equals](#equals)|Compare l'égalité de deux caches.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="sync_sharedallocate"></a><a name="allocate"></a>sync_shared::allocate

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

La fonction membre verrouille le mutex, appelle `cache.allocate(count)`, déverrouille le mutex et retourne le résultat de l’appel précédent à `cache.allocate(count)`. `cache` représente l’objet cache actuel.

## <a name="sync_shareddeallocate"></a><a name="deallocate"></a>sync_shared::dallocate

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

Cette fonction membre verrouille le mutex, appelle `cache.deallocate(ptr, count)`, où `cache` représente l’objet cache, puis déverrouille le mutex.

## <a name="sync_sharedequals"></a><a name="equals"></a>sync_shared::égales

Compare l'égalité de deux caches.

```cpp
bool equals(const sync_shared<Cache>& Other) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Cache*|Type de cache associé au filtre de synchronisation.|
|*Autres*|Cache dont l’égalité est à comparer.|

### <a name="return-value"></a>Valeur de retour

**vrai** si le `cache.equals(Other.cache)`résultat `cache` de , où représente l’objet cache, est **vrai;** autrement, **faux**.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[\<les allocataires>](../standard-library/allocators-header.md)
