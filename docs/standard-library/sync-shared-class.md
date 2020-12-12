---
description: 'En savoir plus sur : classe sync_shared'
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
ms.openlocfilehash: 4093b85ce6f10552cba462074aee2a448cc5ce3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183280"
---
# <a name="sync_shared-class"></a>sync_shared, classe

Décrit un [filtre de synchronisation](../standard-library/allocators-header.md) qui utilise un mutex pour contrôler l’accès à un objet cache partagé par tous les allocateurs.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_shared
```

### <a name="parameters"></a>Paramètres

*En*\
Type de cache associé au filtre de synchronisation. Il peut s’agir [`cache_chunklist`](../standard-library/cache-chunklist-class.md) de, [`cache_freelist`](../standard-library/cache-freelist-class.md) ou [`cache_suballoc`](../standard-library/cache-suballoc-class.md) .

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[lui](#allocate)|Alloue un bloc de mémoire.|
|[libérer](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|
|[equals](#equals)|Compare l'égalité de deux caches.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<allocators>

**Espace de noms :** stdext

## <a name="sync_sharedallocate"></a><a name="allocate"></a> sync_shared :: Allocate

Alloue un bloc de mémoire.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Paramètres

*saut*\
Nombre d’éléments du tableau à allouer.

### <a name="return-value"></a>Valeur renvoyée

Un pointeur vers l’objet alloué.

### <a name="remarks"></a>Notes

La fonction membre verrouille le mutex, appelle `cache.allocate(count)`, déverrouille le mutex et retourne le résultat de l’appel précédent à `cache.allocate(count)`. `cache` représente l’objet cache actuel.

## <a name="sync_shareddeallocate"></a><a name="deallocate"></a> sync_shared ::d eallocate

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

Cette fonction membre verrouille le mutex, appelle `cache.deallocate(ptr, count)`, où `cache` représente l’objet cache, puis déverrouille le mutex.

## <a name="sync_sharedequals"></a><a name="equals"></a> sync_shared :: est égal à

Compare l'égalité de deux caches.

```cpp
bool equals(const sync_shared<Cache>& Other) const;
```

### <a name="parameters"></a>Paramètres

*En*\
Type de cache associé au filtre de synchronisation.

*Autres*\
Cache dont l’égalité est à comparer.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si le résultat de `cache.equals(Other.cache)` , où `cache` représente l’objet de cache, est **`true`** ; sinon, **`false`** .

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)
