---
title: allocator_newdel, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_newdel
- allocators/stdext::allocator_newdel
- stdext::allocators::allocator_newdel
helpviewer_keywords:
- stdext::allocators [C++], allocator_newdel
- stdext::allocator_newdel
ms.assetid: 62666cd2-3afe-49f7-9dd1-9bbbb154da98
ms.openlocfilehash: d49a1596371e4a69873b826d3e756f263539d034
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448307"
---
# <a name="allocatornewdel-class"></a>allocator_newdel, classe

Implémente un allocateur qui utilise l' **opérateur delete** pour libérer un bloc de mémoire et un **nouvel opérateur** pour allouer un bloc de mémoire.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_newdel;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Type*|Type des éléments alloués par l'allocateur.|

## <a name="remarks"></a>Notes

La macro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) transmet cette classe en tant que paramètre *Name* dans l’instruction suivante:`ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`

## <a name="requirements"></a>Configuration requise

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)
