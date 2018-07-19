---
title: allocator_unbounded, classe │ Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
dev_langs:
- C++
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 321737f62d0e2506ef6582f80bed7f398ad5977b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959904"
---
# <a name="allocatorunbounded-class"></a>allocator_unbounded, classe

Décrit un objet qui gère l’allocation de stockage et la libération des objets de type *Type* à l’aide d’un cache de type [cache_freelist](../standard-library/cache-freelist-class.md) avec une longueur gérée par [max_unbounded](../standard-library/max-unbounded-class.md).

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

Le [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) macro transmet cette classe comme le *nom* paramètre dans l’instruction suivante : `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>Configuration requise

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)<br/>
