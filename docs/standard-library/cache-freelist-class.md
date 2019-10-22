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
ms.openlocfilehash: d7840d114acfa0f3daa01c8dfdb6c6114829d93d
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689915"
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
|*SZ*|Nombre d’éléments du tableau à allouer.|
|*Max*|Classe max représentant la taille maximale de la liste de libération. Cette taille peut être [max_fixed_size](../standard-library/max-fixed-size-class.md), [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md) ou [max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Notes

Le modèle de classe cache_freelist conserve une liste libre des blocs de mémoire de taille *SZ*. Lorsque la liste libre est pleine, elle utilise l' **opérateur delete** pour libérer des blocs de mémoire. Lorsque la liste libre est vide, elle utilise **operator new** pour allouer de nouveaux blocs de mémoire. La taille maximale de la liste libre est déterminée par la classe Max Class passée dans le paramètre *Max* .

Chaque bloc de mémoire contient des octets *SZ* de mémoire utilisable et les données que l’opérateur **New** et l' **opérateur delete** requièrent.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[cache_freelist](#cache_freelist)|Construit un objet de type `cache_freelist`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[allocate](#allocate)|Alloue un bloc de mémoire.|
|[deallocate](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|

## <a name="requirements"></a>spécifications

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="allocate"></a>  cache_freelist::allocate

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

## <a name="cache_freelist"></a>  cache_freelist::cache_freelist

Construit un objet de type `cache_freelist`.

```cpp
cache_freelist();
```

### <a name="remarks"></a>Notes

## <a name="deallocate"></a>  cache_freelist::deallocate

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

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)
