---
title: cache_chunklist, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
ms.openlocfilehash: d0dd6176a34bd625069511106c491225d1467d08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366758"
---
# <a name="cache_chunklist-class"></a>cache_chunklist, classe

Définit un [allocateur de blocs](../standard-library/allocators-header.md) qui alloue et désalloue des blocs de mémoire de taille unique.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Sz*|Nombre d’éléments du tableau à allouer.|

## <a name="remarks"></a>Notes

Ce modèle de classe utilise **l’opérateur nouveau** pour allouer des morceaux de mémoire brute, sous-intribuant des blocs pour allouer le stockage pour un bloc de mémoire en cas de besoin; il stocke des blocs de mémoire deallocated dans une liste libre distincte pour chaque morceau, et utilise **l’opérateur supprimer** pour traiter un morceau quand aucun de ses blocs de mémoire est utilisé.

Chaque bloc de mémoire détient des octets *Sz* de mémoire utilisable et un pointeur sur le morceau auquel il appartient. Chaque morceau `Nelts` contient des blocs de mémoire, trois pointeurs, un int et les données que **l’opérateur nouveau** et **l’opérateur supprimer** exigent.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[cache_chunklist](#cache_chunklist)|Construit un objet de type `cache_chunklist`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[Allouer](#allocate)|Alloue un bloc de mémoire.|
|[deallocate](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="cache_chunklistallocate"></a><a name="allocate"></a>cache_chunklist::allocate

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

## <a name="cache_chunklistcache_chunklist"></a><a name="cache_chunklist"></a>cache_chunklist::cache_chunklist

Construit un objet de type `cache_chunklist`.

```cpp
cache_chunklist();
```

### <a name="remarks"></a>Notes

## <a name="cache_chunklistdeallocate"></a><a name="deallocate"></a>cache_chunklist::dallocate

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
