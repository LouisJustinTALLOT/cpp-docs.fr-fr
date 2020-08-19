---
title: cache_suballoc, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
helpviewer_keywords:
- stdext::cache_suballoc
- stdext::cache_suballoc [C++], allocate
- stdext::cache_suballoc [C++], deallocate
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
ms.openlocfilehash: 410cdc7bd45c54c252ce33c7d8e3e2f883ac0eb4
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560619"
---
# <a name="cache_suballoc-class"></a>cache_suballoc, classe

Définit un [allocateur de blocs](../standard-library/allocators-header.md) qui alloue et désalloue des blocs de mémoire de taille unique.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>Paramètres

*SZ*\
Nombre d’éléments du tableau à allouer.

## <a name="remarks"></a>Notes

Le modèle de classe cache_suballoc stocke les blocs de mémoire désalloués dans une liste libre avec une longueur illimitée, à l’aide de et sous- `freelist<sizeof(Type), max_unbounded>` alloue des blocs de mémoire à partir d’un plus grand segment alloué avec l' **opérateur New** lorsque la liste libre est vide.

Chaque bloc contient `Sz * Nelts` des octets de mémoire utilisable et les données que l’opérateur **New** et l' **opérateur delete** requièrent. Les segments alloués ne sont jamais libérés.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[cache_suballoc](#cache_suballoc)|Construit un objet de type `cache_suballoc`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[lui](#allocate)|Alloue un bloc de mémoire.|
|[libérer](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<allocators>

**Espace de noms :** stdext

## <a name="cache_suballocallocate"></a><a name="allocate"></a> cache_suballoc :: Allocate

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

## <a name="cache_suballoccache_suballoc"></a><a name="cache_suballoc"></a> cache_suballoc :: cache_suballoc

Construit un objet de type `cache_suballoc`.

```cpp
cache_suballoc();
```

### <a name="remarks"></a>Notes

## <a name="cache_suballocdeallocate"></a><a name="deallocate"></a> cache_suballoc ::d eallocate

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

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)
