---
title: max_variable_size, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
helpviewer_keywords:
- stdext::max_variable_size
- stdext::max_variable_size [C++], allocated
- stdext::max_variable_size [C++], deallocated
- stdext::max_variable_size [C++], full
- stdext::max_variable_size [C++], released
- stdext::max_variable_size [C++], saved
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
ms.openlocfilehash: 79e37d8c464a009e4a5196aeacc8d4a718e355b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370970"
---
# <a name="max_variable_size-class"></a>max_variable_size, classe

Décrit un objet de [classe max](../standard-library/allocators-header.md) qui limite un objet [freelist](../standard-library/freelist-class.md) à une longueur maximale qui est à peu près proportionnelle au nombre de blocs de mémoire alloués.

## <a name="syntax"></a>Syntaxe

```cpp
class max_variable_size
```

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[max_variable_size](#max_variable_size)|Construit un objet de type `max_variable_size`.|

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

## <a name="max_variable_sizeallocated"></a><a name="allocated"></a>max_variable_size::allocated

Incrémente le nombre de blocs de mémoire alloués.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*_Nx*|Valeur d’incrément.|

### <a name="remarks"></a>Notes

Cette fonction de membre ajoute *_Nx* `_Nallocs`à la valeur stockée . Cette fonction de membre est `cache_freelist::allocate` appelée après chaque appel réussi par l’opérateur **nouveau**. L’argument *_Nx* est le nombre de blocs de mémoire dans le morceau alloué par l’opérateur **nouveau**.

## <a name="max_variable_sizedeallocated"></a><a name="deallocated"></a>max_variable_size::délolocated

Décrémente le nombre de blocs de mémoire alloués.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*_Nx*|Valeur d’incrément.|

### <a name="remarks"></a>Notes

La fonction membre soustrait *_Nx* de `_Nallocs`la valeur stockée . Cette fonction de membre est `cache_freelist::deallocate` appelée après chaque appel par l’opérateur **supprimer**. L’argument *_Nx* est le nombre de blocs de mémoire dans le morceau deallocated par l’opérateur **supprimer**.

## <a name="max_variable_sizefull"></a><a name="full"></a>max_variable_size::plein

Retourne une valeur qui indique si davantage de blocs de mémoire doivent être ajoutés à la liste libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valeur de retour

**vrai** `_Nallocs / 16 + 16 <= _Nblocks`si .

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par `cache_freelist::deallocate`. Si l’appel `deallocate` revient **vrai,** met le bloc de mémoire sur la liste libre; s’il retourne `deallocate` faux, les appels **suppriment** l’opérateur pour régler le bloc.

## <a name="max_variable_sizemax_variable_size"></a><a name="max_variable_size"></a>max_variable_size::max_variable_size

Construit un objet de type `max_variable_size`.

```cpp
max_variable_size();
```

### <a name="remarks"></a>Notes

Le constructeur initialise les valeurs stockées `_Nblocks` et `_Nallocs` à zéro.

## <a name="max_variable_sizereleased"></a><a name="released"></a>max_variable_size::libéré

Décrémente le nombre de blocs de mémoire dans la liste libre.

```cpp
void released();
```

### <a name="remarks"></a>Notes

Cette fonction membre décrémente la valeur stockée `_Nblocks`. La fonction membre `released` de la classe max actuelle est appelée par `cache_freelist::allocate` chaque fois qu’elle supprime un bloc de mémoire de la liste libre.

## <a name="max_variable_sizesaved"></a><a name="saved"></a>max_variable_size::sauvé

Incrémente le nombre de blocs de mémoire dans la liste libre.

```cpp
void saved();
```

### <a name="remarks"></a>Notes

Cette fonction membre incrémente la valeur stockée `_Nblocks`. Cette fonction membre est appelée par `cache_freelist::deallocate` chaque fois qu’elle place un bloc de mémoire dans la liste libre.

## <a name="see-also"></a>Voir aussi

[\<les allocataires>](../standard-library/allocators-header.md)
