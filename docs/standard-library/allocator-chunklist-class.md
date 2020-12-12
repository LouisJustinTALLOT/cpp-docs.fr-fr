---
description: 'En savoir plus sur : classe allocator_chunklist'
title: allocator_chunklist, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_chunklist
- allocators/stdext::allocators::allocator_chunklist
helpviewer_keywords:
- stdext::allocator_chunklist
- stdext::allocators [C++], allocator_chunklist
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
ms.openlocfilehash: 91213b97059f135e0800ae81dd3f6b4966b24c7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163611"
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
