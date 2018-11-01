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
ms.openlocfilehash: 94ae4dfc8f5f9073c0a39f315adfbed3e5c14daf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594569"
---
# <a name="cachechunklist-class"></a>cache_chunklist, classe

Définit un [allocateur de blocs](../standard-library/allocators-header.md) qui alloue et désalloue des blocs de mémoire de taille unique.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*sz*|Nombre d’éléments du tableau à allouer.|

## <a name="remarks"></a>Notes

Cette classe de modèle utilise **opérateur new** pour allouer des segments de mémoire brute, sous-alloue des blocs pour allouer le stockage pour un bloc de mémoire si nécessaire ; il stocke des blocs de mémoire désalloués dans une liste de libération séparée pour chaque segment et utilise **opérateur delete** pour désallouer un segment quand aucun de ses blocs de mémoire est en cours d’utilisation.

Chaque bloc de mémoire contient *Sz* octets de mémoire utilisable et un pointeur vers le segment auquel il appartient. Chaque segment contient `Nelts` blocs de mémoire, trois pointeurs, int et les données qui **opérateur new** et **opérateur delete** nécessitent.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[cache_chunklist](#cache_chunklist)|Construit un objet de type `cache_chunklist`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[allocate](#allocate)|Alloue un bloc de mémoire.|
|[deallocate](#deallocate)|Libère du stockage un nombre d'objets spécifié à partir d'une position spécifiée.|

## <a name="requirements"></a>Configuration requise

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

[\<allocators>](../standard-library/allocators-header.md)<br/>
