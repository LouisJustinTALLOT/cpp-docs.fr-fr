---
description: 'En savoir plus sur : classe allocator_unbounded'
title: allocator_unbounded, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
ms.openlocfilehash: 6d046aa08ddd366c7e7009d1d93c36a365d98170
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163546"
---
# <a name="allocator_unbounded-class"></a>allocator_unbounded, classe

Décrit un objet qui gère l’allocation et la libération de stockage pour les objets *de type type à l’aide* d’un cache de type [cache_freelist](cache-freelist-class.md) avec une longueur gérée par [max_unbounded](max-unbounded-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>Paramètres

*Entrer*\
Type des éléments alloués par l'allocateur.

## <a name="remarks"></a>Notes

La macro [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) transmet cette classe en tant que paramètre *Name* dans l’instruction suivante : `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>Spécifications

**En-tête :**\<allocators>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[\<allocators>](allocators-header.md)
