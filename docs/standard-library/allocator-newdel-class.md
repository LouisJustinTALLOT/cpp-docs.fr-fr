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
ms.openlocfilehash: aa5012f6657b2676756d1d8023274a524b451df3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617464"
---
# <a name="allocator_newdel-class"></a>allocator_newdel, classe

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

La macro [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) transmet cette classe en tant que paramètre *Name* dans l’instruction suivante :`ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`

## <a name="requirements"></a>Configuration requise

**En-tête :**\<allocators>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[\<allocators>](allocators-header.md)
