---
title: cache_freelist, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
ms.openlocfilehash: bbe0ff0f2297afcec99bd162ebe6a6d3e10f9bce
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560724"
---
# <a name="cache_freelist-class"></a>cache_freelist, classe

Définit un [allocateur de blocs](../standard-library/allocators-header.md) qui alloue et désalloue des blocs de mémoire de taille unique.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>Paramètres

*SZ*\
Nombre d’éléments du tableau à allouer.

*Max*\
Classe max représentant la taille maximale de la liste de libération. Cette taille peut être [max_fixed_size](../standard-library/max-fixed-size-class.md), [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md) ou [max_variable_size](../standard-library/max-variable-size-class.md).

## <a name="remarks"></a>Notes

Le modèle de classe cache_freelist conserve une liste libre des blocs de mémoire de taille *SZ*. Lorsque la liste libre est pleine, elle utilise l' **opérateur delete** pour libérer des blocs de mémoire. Lorsque la liste libre est vide, elle utilise **operator new** pour allouer de nouveaux blocs de mémoire. La taille maximale de la liste libre est déterminée par la classe Max Class passée dans le paramètre *Max* .

Chaque bloc de mémoire contient des octets *SZ* de mémoire utilisable et les données que l’opérateur **New** et l' **opérateur delete** requièrent.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[cache_freelist](#cache_freelist)|Construit un objet de type `cache_freelist`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[lui](#allocate)|Alloue un bloc de mémoire.|
|[libérer](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<allocators>

**Espace de noms :** stdext

## <a name="cache_freelistallocate"></a><a name="allocate"></a> cache_freelist :: Allocate

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

## <a name="cache_freelistcache_freelist"></a><a name="cache_freelist"></a> cache_freelist :: cache_freelist

Construit un objet de type `cache_freelist`.

```cpp
cache_freelist();
```

### <a name="remarks"></a>Notes

## <a name="cache_freelistdeallocate"></a><a name="deallocate"></a> cache_freelist ::d eallocate

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
