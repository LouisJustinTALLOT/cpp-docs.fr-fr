---
title: conditional, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: b8f0f69cc1e4f6966bc9ccb63fe529436295badd
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457321"
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

*P*\
Valeur qui détermine le type sélectionné.

*T1*\
Résultat de type quand B a la valeur true.

*H2*\
Résultat de type quand B a la valeur false.

## <a name="remarks"></a>Notes

Le `conditional<B, T1, T2>::type` typedef de membre de modèle prend la valeur *T1* lorsque *b* prend la **valeur true**et prend la valeur *T2* lorsque *b* prend la **valeur false**.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
