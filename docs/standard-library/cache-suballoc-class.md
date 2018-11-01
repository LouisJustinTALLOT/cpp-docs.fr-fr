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
ms.openlocfilehash: 06d0ef390e6ae1980b9ab20b8ceb67213837148b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438868"
---
# <a name="cachesuballoc-class"></a>cache_suballoc, classe

Définit un [allocateur de blocs](../standard-library/allocators-header.md) qui alloue et désalloue des blocs de mémoire de taille unique.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*sz*|Nombre d’éléments du tableau à allouer.|

## <a name="remarks"></a>Notes

La classe de modèle cache_suballoc stocke les blocs de mémoire désalloués dans une liste de libération avec une longueur illimitée, à l’aide de `freelist<sizeof(Type), max_unbounded>`et sous-alloue des blocs de mémoire à partir d’un segment plus grand alloué avec **opérateur new** lorsque la liste de libération est vide.

Chaque segment contient `Sz * Nelts` octets de mémoire utilisable et les données qui **opérateur new** et **opérateur delete** nécessitent. Les segments alloués ne sont jamais libérés.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[cache_suballoc](#cache_suballoc)|Construit un objet de type `cache_suballoc`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[allocate](#allocate)|Alloue un bloc de mémoire.|
|[deallocate](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="allocate"></a>  cache_suballoc::allocate

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

## <a name="cache_suballoc"></a>  cache_suballoc::cache_suballoc

Construit un objet de type `cache_suballoc`.

```cpp
cache_suballoc();
```

### <a name="remarks"></a>Notes

## <a name="deallocate"></a>  cache_suballoc::deallocate

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

[\<allocators>](../standard-library/allocators-header.md)<br/>
