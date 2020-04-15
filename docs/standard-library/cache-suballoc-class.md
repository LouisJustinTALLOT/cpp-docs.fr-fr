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
ms.openlocfilehash: 55860a65fc77f834ed699f3a5114768b7efdde6f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366734"
---
# <a name="cache_suballoc-class"></a>cache_suballoc, classe

Définit un [allocateur de blocs](../standard-library/allocators-header.md) qui alloue et désalloue des blocs de mémoire de taille unique.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Sz*|Nombre d’éléments du tableau à allouer.|

## <a name="remarks"></a>Notes

Le modèle de classe cache_suballoc stocke des blocs de mémoire deallocated `freelist<sizeof(Type), max_unbounded>`dans une liste libre avec une longueur illimitée, en utilisant , et sous-répartit les blocs de mémoire d’un plus grand morceau alloué avec **l’opérateur nouveau** lorsque la liste libre est vide.

Chaque morceau `Sz * Nelts` contient des octets de mémoire utilisable et les données que **l’opérateur nouveau** et **l’opérateur supprimer** exigent. Les segments alloués ne sont jamais libérés.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[cache_suballoc](#cache_suballoc)|Construit un objet de type `cache_suballoc`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[Allouer](#allocate)|Alloue un bloc de mémoire.|
|[deallocate](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="cache_suballocallocate"></a><a name="allocate"></a>cache_suballoc::allocate

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

## <a name="cache_suballoccache_suballoc"></a><a name="cache_suballoc"></a>cache_suballoc::cache_suballoc

Construit un objet de type `cache_suballoc`.

```cpp
cache_suballoc();
```

### <a name="remarks"></a>Notes

## <a name="cache_suballocdeallocate"></a><a name="deallocate"></a>cache_suballoc::dallocate

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
