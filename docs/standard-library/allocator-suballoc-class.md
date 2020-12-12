---
description: 'En savoir plus sur : classe allocator_suballoc'
title: allocator_suballoc, classe
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
ms.openlocfilehash: 7e542b4b8f419f1ac219c63b113aced7e0bd7cda
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163585"
---
# <a name="allocator_suballoc-class"></a>allocator_suballoc, classe

Décrit un objet qui gère l’allocation et la libération de stockage pour les objets *de type type à l’aide* d’un cache de type [cache_suballoc](cache-suballoc-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class allocator_suballoc;
```

### <a name="parameters"></a>Paramètres

*Entrer*\
Type des éléments alloués par l'allocateur.

## <a name="remarks"></a>Notes

La macro [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) transmet cette classe en tant que paramètre *Name* dans l’instruction suivante : `ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>Spécifications

**En-tête :**\<allocators>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[\<allocators>](allocators-header.md)
