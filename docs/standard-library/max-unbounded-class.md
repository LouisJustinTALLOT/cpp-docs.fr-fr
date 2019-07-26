---
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
ms.openlocfilehash: cea2f09837e5efc6969e4ab305d106b9c9728412
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447204"
---
# <a name="maxunbounded-class"></a>max_unbounded, classe

Décrit un objet de [classe max](../standard-library/allocators-header.md) qui ne limite pas la longueur maximale d’un objet [freelist](../standard-library/freelist-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class max_unbounded
```

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

## <a name="allocated"></a>  max_unbounded::allocated

Incrémente le nombre de blocs de mémoire alloués.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*_Nx*|Valeur d’incrément.|

### <a name="remarks"></a>Notes

Cette fonction membre ne fait rien. Elle est appelée après chaque appel `cache_freelist::allocate` réussi de à Operator **New**. L’argument *_Nx* est le nombre de blocs de mémoire dans le segment alloué par Operator **New**.

## <a name="deallocated"></a>  max_unbounded::deallocated

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

## <a name="full"></a>  max_unbounded::full

Retourne une valeur qui indique si davantage de blocs de mémoire doivent être ajoutés à la liste libre.

```cpp
bool full();
```

### <a name="return-value"></a>Valeur de retour

La fonction membre retourne toujours **false**.

### <a name="remarks"></a>Notes

Cette fonction membre est appelée par `cache_freelist::deallocate`. Si l’appel retourne la **valeur true**, `deallocate` place le bloc de mémoire sur la liste libre; si elle `deallocate` retourne la valeur false, appelle l’opérateur **Delete** pour libérer le bloc.

## <a name="released"></a>  max_unbounded::released

Décrémente le nombre de blocs de mémoire dans la liste libre.

```cpp
void released();
```

### <a name="remarks"></a>Notes

Cette fonction membre ne fait rien. La fonction membre `released` de la classe max actuelle est appelée par `cache_freelist::allocate` chaque fois qu’elle supprime un bloc de mémoire de la liste libre.

## <a name="saved"></a>  max_unbounded::saved

Incrémente le nombre de blocs de mémoire dans la liste libre.

```cpp
void saved();
```

### <a name="remarks"></a>Notes

Cette fonction membre ne fait rien. Elle est appelée par `cache_freelist::deallocate` chaque fois qu’elle place un bloc de mémoire dans la liste libre.

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)
