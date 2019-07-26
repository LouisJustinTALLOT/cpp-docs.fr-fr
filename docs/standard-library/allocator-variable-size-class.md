---
title: allocator_variable_size, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_variable_size
- allocators/stdext::allocators::allocator_variable_size
- stdext::allocators::allocator_variable_size
helpviewer_keywords:
- stdext::allocator_variable_size
- stdext::allocators [C++], allocator_variable_size
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
ms.openlocfilehash: bf243089ee8f4e26930e183b007a108e38f444e3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458156"
---
# <a name="allocatorvariablesize-class"></a>allocator_variable_size, classe

Décrit un objet qui gère l’allocation et la libération de stockage pour les objets de type type *à l’aide* d’un cache de type [cache_freelist](../standard-library/cache-freelist-class.md) avec une longueur gérée par [max_variable_size](../standard-library/max-variable-size-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_variable_size;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Type*|Type des éléments alloués par l'allocateur.|

## <a name="remarks"></a>Notes

La macro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) transmet cette classe en tant que paramètre *Name* dans l’instruction suivante:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`

## <a name="requirements"></a>Configuration requise

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)
