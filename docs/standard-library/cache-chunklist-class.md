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
ms.openlocfilehash: 1ee422423356a18f1c81796790593a20dc03fbab
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560711"
---
# <a name="cache_chunklist-class"></a>cache_chunklist, classe

Définit un [allocateur de blocs](../standard-library/allocators-header.md) qui alloue et désalloue des blocs de mémoire de taille unique.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>Paramètres

*SZ*\
Nombre d’éléments du tableau à allouer.

## <a name="remarks"></a>Notes

Ce modèle de classe utilise **operator new** pour allouer des blocs de mémoire brute, sous-allouer des blocs pour allouer du stockage pour un bloc de mémoire si nécessaire. elle stocke les blocs de mémoire désalloués dans une liste de libération distincte pour chaque segment, et utilise l' **opérateur delete** pour libérer un bloc quand aucun de ses blocs de mémoire n’est utilisé.

Chaque bloc de mémoire contient des octets *SZ* de mémoire utilisable et un pointeur vers le segment auquel il appartient. Chaque bloc contient des `Nelts` blocs de mémoire, trois pointeurs, un entier et les données que l' **opérateur New** et l' **opérateur delete** requièrent.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[cache_chunklist](#cache_chunklist)|Construit un objet de type `cache_chunklist`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[lui](#allocate)|Alloue un bloc de mémoire.|
|[libérer](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<allocators>

**Espace de noms :** stdext

## <a name="cache_chunklistallocate"></a><a name="allocate"></a> cache_chunklist :: Allocate

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

## <a name="cache_chunklistcache_chunklist"></a><a name="cache_chunklist"></a> cache_chunklist :: cache_chunklist

Construit un objet de type `cache_chunklist`.

```cpp
cache_chunklist();
```

### <a name="remarks"></a>Notes

## <a name="cache_chunklistdeallocate"></a><a name="deallocate"></a> cache_chunklist ::d eallocate

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
