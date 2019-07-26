---
title: allocator_fixed_size, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_fixed_size
- allocators/stdext::allocator_fixed_size
- stdext::allocators::allocator_fixed_size
helpviewer_keywords:
- stdext::allocators [C++], allocator_fixed_size
- stdext::allocator_fixed_size
ms.assetid: 138f3ef8-b0b3-49c3-9486-58f2213c172f
ms.openlocfilehash: 5ee506838ea723b82f04bba301c19c0149d986bf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451007"
---
# <a name="allocatorfixedsize-class"></a>allocator_fixed_size, classe

Décrit un objet qui gère l’allocation et la libération de stockage pour les objets de type type *à l’aide* d’un cache de type [cache_freelist](../standard-library/cache-freelist-class.md) avec une longueur gérée par [max_fixed_size](../standard-library/max-fixed-size-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_fixed_size;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Type*|Type des éléments alloués par l'allocateur.|

## <a name="remarks"></a>Notes

La macro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) transmet cette classe en tant que paramètre *Name* dans l’instruction suivante:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_fixed_size<10>), SYNC_DEFAULT, allocator_fixed_size);`

## <a name="requirements"></a>Configuration requise

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)
