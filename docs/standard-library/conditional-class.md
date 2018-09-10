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
ms.openlocfilehash: 7a553c2975dd5a58673bd4caa6e7c9ba25d33183
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106611"
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
