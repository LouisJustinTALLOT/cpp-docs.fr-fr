---
title: allocator_chunklist, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_chunklist
- allocators/stdext::allocators::allocator_chunklist
helpviewer_keywords:
- stdext::allocator_chunklist
- stdext::allocators [C++], allocator_chunklist
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
ms.openlocfilehash: 64b419b2565609d8f6018facdbe25d5dee9d94aa
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562621"
---
# <a name="allocator_chunklist-class"></a>allocator_chunklist, classe

Décrit un objet qui gère l’allocation et la libération de stockage pour des objets à l’aide d’un cache de type [cache_chunklist](cache-chunklist-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_chunklist;
```

### <a name="parameters"></a>Paramètres

*Entrer*\
Type des éléments alloués par l'allocateur.

## <a name="remarks"></a>Notes

La macro [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) transmet cette classe en tant que paramètre *Name* dans l’instruction suivante : `ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist);`

## <a name="requirements"></a>Spécifications

**En-tête :**\<allocators>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[\<allocators>](allocators-header.md)
