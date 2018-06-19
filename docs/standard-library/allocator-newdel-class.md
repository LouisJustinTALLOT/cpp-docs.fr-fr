---
title: allocator_newdel, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::allocators::allocator_newdel
- allocators/stdext::allocator_newdel
- stdext::allocators::allocator_newdel
dev_langs:
- C++
helpviewer_keywords:
- stdext::allocators [C++], allocator_newdel
- stdext::allocator_newdel
ms.assetid: 62666cd2-3afe-49f7-9dd1-9bbbb154da98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9eea1a8fe89e9cabcfbe1bf9aa69f1c3fda775c0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33840649"
---
# <a name="allocatornewdel-class"></a>allocator_newdel, classe

Implémente un allocateur qui utilise `operator delete` pour désallouer un bloc de mémoire et `operator new` pour allouer un bloc de mémoire.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_newdel;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`Type`|Type des éléments alloués par l'allocateur.|

## <a name="remarks"></a>Notes

La macro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) transmet cette classe comme paramètre `name` dans l’instruction suivante : `ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`

## <a name="requirements"></a>Spécifications

**En-tête :** \<allocators>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)<br/>
