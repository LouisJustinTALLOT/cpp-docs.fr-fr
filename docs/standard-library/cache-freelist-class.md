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
ms.openlocfilehash: d757909d3e54fed35bf42b943b9f9740dffee115
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366737"
---
# <a name="cache_freelist-class"></a>cache_freelist, classe

Définit un [allocateur de blocs](../standard-library/allocators-header.md) qui alloue et désalloue des blocs de mémoire de taille unique.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Sz*|Nombre d’éléments du tableau à allouer.|
|*Max*|Classe max représentant la taille maximale de la liste de libération. Cette taille peut être [max_fixed_size](../standard-library/max-fixed-size-class.md), [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md) ou [max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Notes

Le modèle de classe cache_freelist maintient une liste libre de blocs de mémoire de taille *Sz*. Lorsque la liste gratuite est complète, elle utilise **l’opérateur supprimer** pour traiter les blocs de mémoire. Lorsque la liste gratuite est vide, elle utilise **l’opérateur nouveau** pour allouer de nouveaux blocs de mémoire. La taille maximale de la liste libre est déterminée par la classe max de classe passée dans le paramètre *Max.*

Chaque bloc mémoire contient des octets *Sz* de mémoire utilisable et les données que **l’opérateur nouveau** et **l’opérateur supprimer** exigent.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[cache_freelist](#cache_freelist)|Construit un objet de type `cache_freelist`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[Allouer](#allocate)|Alloue un bloc de mémoire.|
|[deallocate](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="cache_freelistallocate"></a><a name="allocate"></a>cache_freelist::allocate

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

## <a name="cache_freelistcache_freelist"></a><a name="cache_freelist"></a>cache_freelist::cache_freelist

Construit un objet de type `cache_freelist`.

```cpp
cache_freelist();
```

### <a name="remarks"></a>Notes

## <a name="cache_freelistdeallocate"></a><a name="deallocate"></a>cache_freelist::dallocate

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

## <a name="see-also"></a>Voir aussi

[\<les allocataires>](../standard-library/allocators-header.md)
