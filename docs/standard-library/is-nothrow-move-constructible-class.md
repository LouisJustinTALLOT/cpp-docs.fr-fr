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
ms.openlocfilehash: fbd7ab0593d3a8d6486f2f29cd796656407e14cb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858524"
---
# <a name="isnothrowmoveconstructible-class"></a>is_nothrow_move_constructible, classe

Teste si le type a un constructeur de déplacement **nothrow**.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_nothrow_move_constructible;
```

### <a name="parameters"></a>Paramètres

`Ty` Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type `Ty` a un constructeur de déplacement nothrow. Sinon, sa valeur est false.

## <a name="requirements"></a>Spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
