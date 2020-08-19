---
title: sync_none, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_none
- allocators/stdext::sync_none::allocate
- allocators/stdext::sync_none::deallocate
- allocators/stdext::sync_none::equals
helpviewer_keywords:
- stdext::sync_none
- stdext::sync_none [C++], allocate
- stdext::sync_none [C++], deallocate
- stdext::sync_none [C++], equals
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
ms.openlocfilehash: dac4dc1182de32af485d37a00ff96370ea8d8943
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562114"
---
# <a name="sync_none-class"></a>sync_none, classe

Décrit un [filtre de synchronisation](../standard-library/allocators-header.md) qui ne fournit aucune synchronisation.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_none
```

### <a name="parameters"></a>Paramètres

`Cache`\
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

## <a name="sync_noneallocate"></a><a name="allocate"></a> sync_none :: Allocate

Alloue un bloc de mémoire.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Paramètres

*saut*\
Nombre d’éléments du tableau à allouer.

### <a name="remarks"></a>Notes

La fonction membre retourne `cache.allocate(count)`, où `cache` est l’objet cache.

## <a name="sync_nonedeallocate"></a><a name="deallocate"></a> sync_none ::d eallocate

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

La fonction membre appelle `cache.deallocate(ptr, count)`, où `cache` représente l’objet cache.

## <a name="sync_noneequals"></a><a name="equals"></a> sync_none :: est égal à

Compare l'égalité de deux caches.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>Paramètres

*En*\
L’objet cache du filtre de synchronisation.

*Autres*\
Objet cache dont l’égalité est à comparer.

### <a name="return-value"></a>Valeur de retour

La fonction membre retourne toujours **`true`** .

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)
