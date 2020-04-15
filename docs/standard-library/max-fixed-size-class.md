---
title: max_fixed_size, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_fixed_size
- allocators/stdext::max_fixed_size::allocated
- allocators/stdext::max_fixed_size::deallocated
- allocators/stdext::max_fixed_size::full
- allocators/stdext::max_fixed_size::released
- allocators/stdext::max_fixed_size::saved
helpviewer_keywords:
- stdext::max_fixed_size
- stdext::max_fixed_size [C++], allocated
- stdext::max_fixed_size [C++], deallocated
- stdext::max_fixed_size [C++], full
- stdext::max_fixed_size [C++], released
- stdext::max_fixed_size [C++], saved
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
ms.openlocfilehash: 7f75dd71caa3cfcfec19264b1da62c6d47a3e01d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371007"
---
# <a name="max_fixed_size-class"></a>max_fixed_size, classe

Décrit un objet de [classe max](../standard-library/allocators-header.md) qui limite un objet [freelist](../standard-library/freelist-class.md) à une longueur maximale fixe.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Max*|Classe maximale qui détermine le nombre maximal d’éléments à stocker dans la `freelist`.|

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[max_fixed_size](#max_fixed_size)|Construit un objet de type `max_fixed_size`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[allocated](#allocated)|Incrémente le nombre de blocs de mémoire alloués.|
|[deallocated](#deallocated)|Décrémente le nombre de blocs de mémoire alloués.|
|[Plein](#full)|Retourne une valeur qui indique si davantage de blocs de mémoire doivent être ajoutés à la liste libre.|
|[Libéré](#released)|Décrémente le nombre de blocs de mémoire dans la liste libre.|
|[saved](#saved)|Incrémente le nombre de blocs de mémoire dans la liste libre.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="max_fixed_sizeallocated"></a><a name="allocated"></a>max_fixed_size::allocated

Incrémente le nombre de blocs de mémoire alloués.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*_Nx*|Valeur d’incrément.|

### <a name="remarks"></a>Notes

La fonction membre ne fait rien. Cette fonction de membre est `cache_freelist::allocate` appelée après chaque appel réussi par l’opérateur **nouveau**. L’argument *_Nx* est le nombre de blocs de mémoire dans le morceau alloué par l’opérateur **nouveau**.

## <a name="max_fixed_sizedeallocated"></a><a name="deallocated"></a>max_fixed_size::délolocated

Décrémente le nombre de blocs de mémoire alloués.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*_Nx*|Valeur d’incrément.|

### <a name="remarks"></a>Notes

La fonction membre ne fait rien. Cette fonction de membre est `cache_freelist::deallocate` appelée après chaque appel par l’opérateur **supprimer**. L’argument *_Nx* est le nombre de blocs de mémoire dans le morceau deallocated par l’opérateur **supprimer**.

## <a name="max_fixed_sizefull"></a><a name="full"></a>max_fixed_size::plein

Retourne une valeur qui indique si davantage de blocs de mémoire doivent être ajoutés à la liste libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valeur de retour

**vrai** `Max <= _Nblocks`si ; autrement, **faux**.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par `cache_freelist::deallocate`. Si l’appel `deallocate` revient **vrai,** met le bloc de mémoire sur la liste libre; s’il retourne `deallocate` faux, les appels **suppriment** l’opérateur pour régler le bloc.

## <a name="max_fixed_sizemax_fixed_size"></a><a name="max_fixed_size"></a>max_fixed_size::max_fixed_size

Construit un objet de type `max_fixed_size`.

```cpp
max_fixed_size();
```

### <a name="remarks"></a>Notes

Ce constructeur initialise la valeur stockée `_Nblocks` à zéro.

## <a name="max_fixed_sizereleased"></a><a name="released"></a>max_fixed_size::libéré

Décrémente le nombre de blocs de mémoire dans la liste libre.

```cpp
void released();
```

### <a name="remarks"></a>Notes

Décrémente la valeur stockée `_Nblocks`. La `released` fonction de membre de la `cache_freelist::allocate` classe [max](../standard-library/allocators-header.md) actuelle est appelée par chaque fois qu’il supprime un bloc de mémoire de la liste libre.

## <a name="max_fixed_sizesaved"></a><a name="saved"></a>max_fixed_size::sauvé

Incrémente le nombre de blocs de mémoire dans la liste libre.

```cpp
void saved();
```

### <a name="remarks"></a>Notes

Cette fonction membre incrémente la valeur stockée `_Nblocks`. Cette fonction membre est appelée par `cache_freelist::deallocate` chaque fois qu’elle place un bloc de mémoire dans la liste libre.

## <a name="see-also"></a>Voir aussi

[\<les allocataires>](../standard-library/allocators-header.md)
