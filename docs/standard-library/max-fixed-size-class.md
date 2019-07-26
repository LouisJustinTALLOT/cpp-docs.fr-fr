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
ms.openlocfilehash: bbc39a169f9a4bbac3e78b208b3a1a31e4e30ff2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456377"
---
# <a name="maxfixedsize-class"></a>max_fixed_size, classe

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

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[allocated](#allocated)|Incrémente le nombre de blocs de mémoire alloués.|
|[deallocated](#deallocated)|Décrémente le nombre de blocs de mémoire alloués.|
|[full](#full)|Retourne une valeur qui indique si davantage de blocs de mémoire doivent être ajoutés à la liste libre.|
|[released](#released)|Décrémente le nombre de blocs de mémoire dans la liste libre.|
|[saved](#saved)|Incrémente le nombre de blocs de mémoire dans la liste libre.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="allocated"></a>  max_fixed_size::allocated

Incrémente le nombre de blocs de mémoire alloués.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*_Nx*|Valeur d’incrément.|

### <a name="remarks"></a>Notes

La fonction membre ne fait rien. Cette fonction membre est appelée après chaque appel `cache_freelist::allocate` réussi de à Operator **New**. L’argument *_Nx* est le nombre de blocs de mémoire dans le segment alloué par Operator **New**.

## <a name="deallocated"></a>  max_fixed_size::deallocated

Décrémente le nombre de blocs de mémoire alloués.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*_Nx*|Valeur d’incrément.|

### <a name="remarks"></a>Notes

La fonction membre ne fait rien. Cette fonction membre est appelée après chaque appel de `cache_freelist::deallocate` à l’opérateur **Delete**. L’argument *_Nx* est le nombre de blocs de mémoire dans le segment libérés par l’opérateur **Delete**.

## <a name="full"></a>  max_fixed_size::full

Retourne une valeur qui indique si davantage de blocs de mémoire doivent être ajoutés à la liste libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valeur de retour

**true** si `Max <= _Nblocks`; sinon, **false**.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par `cache_freelist::deallocate`. Si l’appel retourne la **valeur true**, `deallocate` place le bloc de mémoire sur la liste libre; si elle `deallocate` retourne la valeur false, appelle l’opérateur **Delete** pour libérer le bloc.

## <a name="max_fixed_size"></a>  max_fixed_size::max_fixed_size

Construit un objet de type `max_fixed_size`.

```cpp
max_fixed_size();
```

### <a name="remarks"></a>Notes

Ce constructeur initialise la valeur stockée `_Nblocks` à zéro.

## <a name="released"></a>  max_fixed_size::released

Décrémente le nombre de blocs de mémoire dans la liste libre.

```cpp
void released();
```

### <a name="remarks"></a>Notes

Décrémente la valeur stockée `_Nblocks`. La fonction membre `released` de la [classe max](../standard-library/allocators-header.md) actuelle est appelée par `cache_freelist::allocate` chaque fois qu’elle supprime un bloc de mémoire de la liste libre.

## <a name="saved"></a>  max_fixed_size::saved

Incrémente le nombre de blocs de mémoire dans la liste libre.

```cpp
void saved();
```

### <a name="remarks"></a>Notes

Cette fonction membre incrémente la valeur stockée `_Nblocks`. Cette fonction membre est appelée par `cache_freelist::deallocate` chaque fois qu’elle place un bloc de mémoire dans la liste libre.

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)
