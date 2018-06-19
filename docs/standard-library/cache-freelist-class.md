---
title: cache_freelist, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
dev_langs:
- C++
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8478490914a6f9049cd54ec78c8de8a1e519f36f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845672"
---
# <a name="cachefreelist-class"></a>cache_freelist, classe

Définit un [allocateur de blocs](../standard-library/allocators-header.md) qui alloue et désalloue des blocs de mémoire de taille unique.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`Sz`|Nombre d’éléments du tableau à allouer.|
|`Max`|Classe max représentant la taille maximale de la liste de libération. Cette taille peut être [max_fixed_size](../standard-library/max-fixed-size-class.md), [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md) ou [max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Notes

La classe de modèle cache_freelist conserve une liste de libération des blocs de mémoire de taille `Sz`. Quand la liste de libération est pleine, elle utilise `operator delete` pour désallouer des blocs de mémoire. Quand la liste de libération est vide, elle utilise `operator new` pour allouer de nouveaux blocs de mémoire. La taille maximale de la liste de libération est déterminée par la classe max passée dans le paramètre `Max`.

Chaque bloc de mémoire contient `Sz` octets de mémoire utilisable et les données dont `operator new` et `operator delete` ont besoin.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[cache_freelist](#cache_freelist)|Construit un objet de type `cache_freelist`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[allocate](#allocate)|Alloue un bloc de mémoire.|
|[deallocate](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|

## <a name="requirements"></a>Spécifications

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
|`count`|Nombre d’éléments du tableau à allouer.|

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
|`ptr`|Pointeur vers le premier objet à désallouer dans le stockage.|
|`count`|Nombre d’objets à désallouer dans le stockage.|

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)<br/>
