---
title: allocator_unbounded, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
ms.openlocfilehash: 38ecec3848808585ac0ed7cb1b076480a79f6d41
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448298"
---
# <a name="allocatorunbounded-class"></a>allocator_unbounded, classe

Décrit un objet qui gère l’allocation et la libération de stockage pour les objets de type type *à l’aide* d’un cache de type [cache_freelist](../standard-library/cache-freelist-class.md) avec une longueur gérée par [max_unbounded](../standard-library/max-unbounded-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Type*|Type des éléments alloués par l'allocateur.|

## <a name="remarks"></a>Notes

La macro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) transmet cette classe en tant que paramètre *Name* dans l’instruction suivante:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>Configuration requise

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)
