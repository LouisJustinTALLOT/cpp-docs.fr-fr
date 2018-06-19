---
title: max_fixed_size, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::max_fixed_size
- allocators/stdext::max_fixed_size::allocated
- allocators/stdext::max_fixed_size::deallocated
- allocators/stdext::max_fixed_size::full
- allocators/stdext::max_fixed_size::released
- allocators/stdext::max_fixed_size::saved
dev_langs:
- C++
helpviewer_keywords:
- stdext::max_fixed_size
- stdext::max_fixed_size [C++], allocated
- stdext::max_fixed_size [C++], deallocated
- stdext::max_fixed_size [C++], full
- stdext::max_fixed_size [C++], released
- stdext::max_fixed_size [C++], saved
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0e1e57693650c69aa1a5b8ec006830458ef7775
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854192"
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
|`Max`|Classe maximale qui détermine le nombre maximal d’éléments à stocker dans la `freelist`.|

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

## <a name="requirements"></a>Spécifications

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
|`_Nx`|Valeur d’incrément.|

### <a name="remarks"></a>Notes

La fonction membre ne fait rien. Cette fonction membre est appelée après chaque appel réussi par `cache_freelist::allocate` à l’opérateur `new`. L’argument `_Nx` est le nombre de blocs de mémoire dans le bloc alloués par l’opérateur `new`.

## <a name="deallocated"></a>  max_fixed_size::deallocated

Décrémente le nombre de blocs de mémoire alloués.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`_Nx`|Valeur d’incrément.|

### <a name="remarks"></a>Notes

La fonction membre ne fait rien. Cette fonction membre est appelée après chaque appel par `cache_freelist::deallocate` à l’opérateur `delete`. L’argument `_Nx` est le nombre de blocs de mémoire dans le bloc libérés par l’opérateur `delete`.

## <a name="full"></a>  max_fixed_size::full

Retourne une valeur qui indique si davantage de blocs de mémoire doivent être ajoutés à la liste libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valeur de retour

`true` si `Max <= _Nblocks` ; sinon, `false`.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par `cache_freelist::deallocate`. Si l’appel retourne `true`, `deallocate` place le bloc de mémoire dans la liste libre ; s’il retourne false, `deallocate` appelle l’opérateur `delete` pour libérer le bloc.

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

[\<allocators>](../standard-library/allocators-header.md)<br/>
