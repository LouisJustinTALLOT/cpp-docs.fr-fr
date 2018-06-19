---
title: sync_none, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_none
- allocators/stdext::sync_none::allocate
- allocators/stdext::sync_none::deallocate
- allocators/stdext::sync_none::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::sync_none
- stdext::sync_none [C++], allocate
- stdext::sync_none [C++], deallocate
- stdext::sync_none [C++], equals
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 540f5085d1f2ab3b641e023654d05f1e9e66bae2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857335"
---
# <a name="syncnone-class"></a>sync_none, classe

Décrit un [filtre de synchronisation](../standard-library/allocators-header.md) qui ne fournit aucune synchronisation.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_none
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`Cache`|Type de cache associé au filtre de synchronisation. Il peut s’agir de [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) ou [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[allocate](#allocate)|Alloue un bloc de mémoire.|
|[deallocate](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|
|[equals](#equals)|Compare l'égalité de deux caches.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="allocate"></a>  sync_none::allocate

Alloue un bloc de mémoire.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`count`|Nombre d’éléments du tableau à allouer.|

### <a name="remarks"></a>Notes

La fonction membre retourne `cache.allocate(count)`, où `cache` est l’objet cache.

## <a name="deallocate"></a>  sync_none::deallocate

Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`ptr`|Pointeur vers le premier objet à désallouer dans le stockage.|
|`count`|Nombre d’objets à désallouer dans le stockage.|

### <a name="remarks"></a>Notes

La fonction membre appelle `cache.deallocate(ptr, count)`, où `cache` représente l’objet cache.

## <a name="equals"></a>  sync_none::equals

Compare l'égalité de deux caches.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`Cache`|L’objet cache du filtre de synchronisation.|
|`Other`|Objet cache dont l’égalité est à comparer.|

### <a name="return-value"></a>Valeur de retour

La fonction membre retourne toujours `true`.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)<br/>
