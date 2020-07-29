---
title: is_nothrow_assignable, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_assignable
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
ms.openlocfilehash: 7130079ff58820ec5a8893fd248c5b98fc10c93c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222366"
---
# <a name="is_nothrow_assignable-class"></a>is_nothrow_assignable, classe

Teste si une valeur *de de type peut* être assignée à un type et que l’assignation est *connue comme ne* levant pas d’exception.

## <a name="syntax"></a>Syntaxe

```cpp
template <class To, class From>
struct is_nothrow_assignable;
```

### <a name="parameters"></a>Paramètres

*À*\
Type de l'objet qui reçoit l'assignation.

*De*\
Type de l'objet qui fournit la valeur.

## <a name="remarks"></a>Notes

L’expression `declval<To>() = declval<From>()` doit être bien formée et le compilateur doit savoir qu’elle ne lève pas d’exception. *From* et *to* doivent tous deux être des types complets, **`void`** , ou des tableaux de limites inconnues.

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
