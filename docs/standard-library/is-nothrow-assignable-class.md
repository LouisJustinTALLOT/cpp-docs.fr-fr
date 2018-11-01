---
title: is_nothrow_assignable, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_assignable
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
ms.openlocfilehash: c59c3623f9c9548a7b7e59d0c56a2acd4d3883a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652448"
---
# <a name="isnothrowassignable-class"></a>is_nothrow_assignable, classe

Teste si une valeur de *de* type peut être affecté à *à* type et l’affectation ne connaît ne pas lever.

## <a name="syntax"></a>Syntaxe

```cpp
template <class To, class From>
struct is_nothrow_assignable;
```

### <a name="parameters"></a>Paramètres

*To*<br/>
Type de l'objet qui reçoit l'assignation.

*From*<br/>
Type de l'objet qui fournit la valeur.

## <a name="remarks"></a>Notes

L’expression `declval<To>() = declval<From>()` doit être bien formée et le compilateur doit savoir qu’elle ne lève pas d’exception. Les deux *de* et *à* doivent être des types complets, **void**, ou des tableaux de limite inconnue.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
