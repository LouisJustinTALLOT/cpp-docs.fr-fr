---
title: is_nothrow_move_constructible, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_move_constructible
ms.assetid: d186d97b-7b89-470a-8d30-993046a83379
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1883f051a1df74256da533cf2aba19626b9f19e
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959457"
---
# <a name="isnothrowmoveconstructible-class"></a>is_nothrow_move_constructible, classe

Teste si le type a un constructeur de déplacement **nothrow**.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_nothrow_move_constructible;
```

### <a name="parameters"></a>Paramètres

*Ty* type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *Ty* a un constructeur de déplacement nothrow, sinon, sa valeur est false.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
