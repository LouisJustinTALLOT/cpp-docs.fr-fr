---
title: is_assignable, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_assignable
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
ms.openlocfilehash: 33b0ce6112119c935ff70e5d619b284acc6ee8c2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456666"
---
# <a name="isassignable-class"></a>is_assignable, classe

Teste si une valeur de type `From` peut être affectée à un type `To`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Paramètres

*À*\
Type de l'objet qui reçoit l'assignation.

*De*\
Type de l'objet qui fournit la valeur.

## <a name="remarks"></a>Notes

L’expression non évaluée `declval<To>() = declval<From>()` doit être bien formée. Et doivent être des types complets, void ou des tableaux de limites inconnues.  `From` `To`

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
