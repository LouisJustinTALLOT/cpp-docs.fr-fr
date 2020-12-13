---
description: 'En savoir plus sur : classe max_unbounded'
title: max_unbounded, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_unbounded
- allocators/stdext::max_unbounded::allocated
- allocators/stdext::max_unbounded::deallocated
- allocators/stdext::max_unbounded::full
- allocators/stdext::max_unbounded::released
- allocators/stdext::max_unbounded::saved
helpviewer_keywords:
- stdext::max_unbounded
- stdext::max_unbounded [C++], allocated
- stdext::max_unbounded [C++], deallocated
- stdext::max_unbounded [C++], full
- stdext::max_unbounded [C++], released
- stdext::max_unbounded [C++], saved
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
ms.openlocfilehash: 64501d9028b5adba0f9e3059f3581ad57d00ea27
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97149238"
---
# <a name="max_unbounded-class"></a>max_unbounded, classe

Décrit un objet de [classe max](../standard-library/allocators-header.md) qui ne limite pas la longueur maximale d’un objet [freelist](../standard-library/freelist-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class max_unbounded
```

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

## <a name="max_unboundedallocated"></a><a name="allocated"></a> max_unbounded :: allouée

Incrémente le nombre de blocs de mémoire alloués.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Paramètres

*_Nx*\
Valeur d’incrément.

### <a name="remarks"></a>Notes

Cette fonction membre ne fait rien. Elle est appelée après chaque appel réussi par `cache_freelist::allocate` à l’opérateur **`new`** . L’argument *_Nx* est le nombre de blocs de mémoire dans le segment alloué par l’opérateur **`new`** .

## <a name="max_unboundeddeallocated"></a><a name="deallocated"></a> max_unbounded ::d eallocated

Décrémente le nombre de blocs de mémoire alloués.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Paramètres

*_Nx*\
Valeur d’incrément.

### <a name="remarks"></a>Notes

La fonction membre ne fait rien. Cette fonction membre est appelée après chaque appel par `cache_freelist::deallocate` à l’opérateur **`delete`** . L’argument *_Nx* est le nombre de blocs de mémoire dans le segment libéré par l’opérateur **`delete`** .

## <a name="max_unboundedfull"></a><a name="full"></a> max_unbounded :: Full

Retourne une valeur qui indique si davantage de blocs de mémoire doivent être ajoutés à la liste libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valeur renvoyée

La fonction membre retourne toujours **`false`** .

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par `cache_freelist::deallocate`. Si l’appel retourne **`true`** `deallocate` la valeur, place le bloc de mémoire sur la liste libre ; si elle retourne false, `deallocate` appelle l’opérateur **`delete`** pour libérer le bloc.

## <a name="max_unboundedreleased"></a><a name="released"></a> max_unbounded :: relâché

Décrémente le nombre de blocs de mémoire dans la liste libre.

```cpp
void released();
```

### <a name="remarks"></a>Notes

Cette fonction membre ne fait rien. La fonction membre `released` de la classe max actuelle est appelée par `cache_freelist::allocate` chaque fois qu’elle supprime un bloc de mémoire de la liste libre.

## <a name="max_unboundedsaved"></a><a name="saved"></a> max_unbounded :: saved

Incrémente le nombre de blocs de mémoire dans la liste libre.

```cpp
void saved();
```

### <a name="remarks"></a>Notes

Cette fonction membre ne fait rien. Elle est appelée par `cache_freelist::deallocate` chaque fois qu’elle place un bloc de mémoire dans la liste libre.

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)
