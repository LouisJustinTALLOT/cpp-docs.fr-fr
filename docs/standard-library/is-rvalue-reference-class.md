---
title: is_rvalue_reference, classe │ Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_rvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- is_rvalue_reference class
- is_rvalue_reference
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acba0f78df8cc537aecd5d2fc33380e4674e5721
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956919"
---
# <a name="isrvaluereference-class"></a>is_rvalue_reference, classe

Teste si le type est une référence rvalue.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_rvalue_reference;
```

### <a name="parameters"></a>Paramètres

*Ty* type à interroger.

## <a name="remarks"></a>Notes

Une instance de ce prédicat de type a la valeur true si le type *Ty* est un [référence rvalue](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[Lvalues et Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
