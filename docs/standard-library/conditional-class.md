---
title: conditional, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::conditional
dev_langs:
- C++
helpviewer_keywords:
- conditional class
- conditional
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d51397080267dd50f012b274e95ac4c9aa4fa64
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841874"
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

`B` La valeur qui détermine le type sélectionné.

`T1` Résultat de type quand B a la valeur true.

`T2` Résultat de type quand B a la valeur false.

## <a name="remarks"></a>Notes

Le typedef de membre de modèle `conditional<B, T1, T2>::type` équivaut à `T1` quand `B` équivaut à `true`, et équivaut à `T2` quand `B` équivaut à `false`.

## <a name="requirements"></a>Spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
