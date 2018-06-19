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
ms.openlocfilehash: 0b8645e9ac8a8d3e8f40590105df234b4ef55bac
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857062"
---
# <a name="isrvaluereference-class"></a>is_rvalue_reference, classe

Teste si le type est une référence rvalue.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_rvalue_reference;
```

### <a name="parameters"></a>Paramètres

`Ty` Type à interroger.

## <a name="remarks"></a>Notes

Une instance de ce prédicat de type a la valeur true si le type `Ty` est une [référence rvalue](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[Lvalues et Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
