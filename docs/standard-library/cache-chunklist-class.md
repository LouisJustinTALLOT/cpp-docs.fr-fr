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
ms.openlocfilehash: 035e5153b4e4c84743a64bcc9cec24920a6a0336
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688367"
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
|*SZ*|Nombre d’éléments du tableau à allouer.|

## <a name="remarks"></a>Notes

Ce modèle de classe utilise **operator new** pour allouer des blocs de mémoire brute, sous-allouer des blocs pour allouer du stockage pour un bloc de mémoire si nécessaire. elle stocke les blocs de mémoire désalloués dans une liste de libération distincte pour chaque segment, et utilise l' **opérateur delete** pour libérer un bloc quand aucun de ses blocs de mémoire n’est utilisé.

Chaque bloc de mémoire contient des octets *SZ* de mémoire utilisable et un pointeur vers le segment auquel il appartient. Chaque bloc contient des blocs de mémoire `Nelts`, trois pointeurs, un entier et les données que l' **opérateur New** et l' **opérateur delete** requièrent.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[cache_chunklist](#cache_chunklist)|Construit un objet de type `cache_chunklist`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[allocate](#allocate)|Alloue un bloc de mémoire.|
|[deallocate](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|

## <a name="requirements"></a>spécifications

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="allocate"></a>  cache_chunklist::allocate

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

## <a name="cache_chunklist"></a>  cache_chunklist::cache_chunklist

Construit un objet de type `cache_chunklist`.

```cpp
cache_chunklist();
```

### <a name="remarks"></a>Notes

## <a name="deallocate"></a>  cache_chunklist::deallocate

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
