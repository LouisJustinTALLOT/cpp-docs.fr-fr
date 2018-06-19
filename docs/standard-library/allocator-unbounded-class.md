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
ms.openlocfilehash: 0108b8d02c275cb4e498cd3e9df00b87b7cae28f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33840496"
---
# <a name="allocatorunbounded-class"></a>allocator_unbounded, classe

Décrit un objet qui gère l’allocation et la libération de stockage pour des objets de type `Type` à l’aide d’un cache de type [cache_freelist](../standard-library/cache-freelist-class.md) avec une longueur gérée par [max_unbounded](../standard-library/max-unbounded-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`Type`|Type des éléments alloués par l'allocateur.|

## <a name="remarks"></a>Notes

La macro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) transmet cette classe comme paramètre `name` dans l’instruction suivante : `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>Spécifications

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)<br/>
