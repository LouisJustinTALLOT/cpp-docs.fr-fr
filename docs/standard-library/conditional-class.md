---
title: conditional, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: be81a1bc32f2f86f1d79970868933bddb8dc3620
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523017"
---
# <a name="conditional-class"></a>conditional, classe

Sélectionne un des deux types, selon la condition spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
template <bool B, class T1, class T2>
struct conditional;

template <bool _Test, class _T1, class _T2>
using conditional_t = typename conditional<_Test, _T1, _T2>::type;
```

### <a name="parameters"></a>Paramètres

*B*<br/>
Valeur qui détermine le type sélectionné.

*T1*<br/>
Résultat de type quand B a la valeur true.

*T2*<br/>
Résultat de type quand B a la valeur false.

## <a name="remarks"></a>Notes

Le typedef de membre de modèle `conditional<B, T1, T2>::type` prend la valeur *T1* lorsque *B* prend la valeur **true**et prend la valeur *T2* lorsque  *B* prend la valeur **false**.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
