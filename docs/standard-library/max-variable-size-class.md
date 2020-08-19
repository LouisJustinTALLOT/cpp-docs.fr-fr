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
ms.openlocfilehash: 53d2603c82e94710ed687dce4caeec24aeb2f60a
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561646"
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
|[désalloué](#deallocated)|Décrémente le nombre de blocs de mémoire alloués.|
|[full](#full)|Retourne une valeur qui indique si davantage de blocs de mémoire doivent être ajoutés à la liste libre.|
|[incluses](#released)|Décrémente le nombre de blocs de mémoire dans la liste libre.|
|[saved](#saved)|Incrémente le nombre de blocs de mémoire dans la liste libre.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<allocators>

**Espace de noms :** stdext

## <a name="max_variable_sizeallocated"></a><a name="allocated"></a> max_variable_size :: allouée

Incrémente le nombre de blocs de mémoire alloués.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Paramètres

*_Nx*\
Valeur d’incrément.

### <a name="remarks"></a>Notes

Cette fonction membre ajoute *_Nx* à la valeur stockée `_Nallocs` . Cette fonction membre est appelée après chaque appel réussi par `cache_freelist::allocate` à l’opérateur **`new`** . L’argument *_Nx* est le nombre de blocs de mémoire dans le segment alloué par l’opérateur **`new`** .

## <a name="max_variable_sizedeallocated"></a><a name="deallocated"></a> max_variable_size ::d eallocated

Décrémente le nombre de blocs de mémoire alloués.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Paramètres

*_Nx*\
Valeur d’incrément.

### <a name="remarks"></a>Notes

La fonction membre soustrait *_Nx* de la valeur stockée `_Nallocs` . Cette fonction membre est appelée après chaque appel par `cache_freelist::deallocate` à l’opérateur **`delete`** . L’argument *_Nx* est le nombre de blocs de mémoire dans le segment libéré par l’opérateur **`delete`** .

## <a name="max_variable_sizefull"></a><a name="full"></a> max_variable_size :: Full

Retourne une valeur qui indique si davantage de blocs de mémoire doivent être ajoutés à la liste libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valeur de retour

**`true`** Si `_Nallocs / 16 + 16 <= _Nblocks` .

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par `cache_freelist::deallocate`. Si l’appel retourne **`true`** `deallocate` la valeur, place le bloc de mémoire sur la liste libre ; si elle retourne false, `deallocate` appelle l’opérateur **`delete`** pour libérer le bloc.

## <a name="max_variable_sizemax_variable_size"></a><a name="max_variable_size"></a> max_variable_size :: max_variable_size

Construit un objet de type `max_variable_size`.

```cpp
max_variable_size();
```

### <a name="remarks"></a>Notes

Le constructeur initialise les valeurs stockées `_Nblocks` et `_Nallocs` à zéro.

## <a name="max_variable_sizereleased"></a><a name="released"></a> max_variable_size :: relâché

Décrémente le nombre de blocs de mémoire dans la liste libre.

```cpp
void released();
```

### <a name="remarks"></a>Notes

Cette fonction membre décrémente la valeur stockée `_Nblocks`. La fonction membre `released` de la classe max actuelle est appelée par `cache_freelist::allocate` chaque fois qu’elle supprime un bloc de mémoire de la liste libre.

## <a name="max_variable_sizesaved"></a><a name="saved"></a> max_variable_size :: saved

Incrémente le nombre de blocs de mémoire dans la liste libre.

```cpp
void saved();
```

### <a name="remarks"></a>Notes

Cette fonction membre incrémente la valeur stockée `_Nblocks`. Cette fonction membre est appelée par `cache_freelist::deallocate` chaque fois qu’elle place un bloc de mémoire dans la liste libre.

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)
