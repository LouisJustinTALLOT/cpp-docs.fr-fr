---
title: sync_per_container, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
ms.openlocfilehash: d38307c4ae19e5f87d0dbcca8943dc1c3f239917
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232896"
---
# <a name="sync_per_container-class"></a>sync_per_container, classe

Décrit un [filtre de synchronisation](../standard-library/allocators-header.md) qui fournit un objet cache distinct pour chaque objet allocateur.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_per_container
    : public Cache
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Cache*|Type de cache associé au filtre de synchronisation. Il peut s’agir de [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) ou [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[equals](#equals)|Compare l'égalité de deux caches.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<allocators>

**Espace de noms :** stdext

## <a name="sync_per_containerequals"></a><a name="equals"></a>sync_per_container :: est égal à

Compare l'égalité de deux caches.

```cpp
bool equals(const sync_per_container<Cache>& Other) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Cache*|L’objet cache du filtre de synchronisation.|
|*Autres*|Objet cache dont l’égalité est à comparer.|

### <a name="return-value"></a>Valeur de retour

La fonction membre retourne toujours **`false`** .

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)
