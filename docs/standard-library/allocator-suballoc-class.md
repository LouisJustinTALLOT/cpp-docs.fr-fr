---
title: allocator_suballoc, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
ms.openlocfilehash: 3e5b69ef3f47a173ef768283bbae4f6e3b5f5190
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458145"
---
# <a name="allocatorsuballoc-class"></a>allocator_suballoc, classe

Décrit un objet qui gère l’allocation et la libération de stockage pour les objets de type *type à l'* aide d’un cache de type [cache_suballoc](../standard-library/cache-suballoc-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_suballoc;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Type*|Type des éléments alloués par l'allocateur.|

## <a name="remarks"></a>Notes

La macro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) transmet cette classe en tant que paramètre *Name* dans l’instruction suivante:`ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>Configuration requise

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)
