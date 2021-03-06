---
description: 'En savoir plus sur : classe conditionnelle'
title: conditional, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::conditional
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
ms.openlocfilehash: f8edbd7341598957ecbe8b0822a832973f0e06a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324969"
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

Le typedef de membre `conditional<B, T1, T2>::type` de modèle prend la valeur *T1* lorsque *b* prend la valeur **`true`** , et prend la valeur *T2* lorsque *b* prend la valeur **`false`** .

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
