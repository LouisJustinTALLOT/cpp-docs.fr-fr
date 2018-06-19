---
title: is_trivially_constructible, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 757a5eb526bc8d4294a64cbdc9645e72285162ce
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857257"
---
# <a name="istriviallyconstructible-class"></a>is_trivially_constructible, classe

Teste si un type est constructible de façon triviale quand les types d’arguments spécifiés sont utilisés.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>Paramètres

`T` Type à interroger.

`Args` Les types d’arguments à faire correspondre dans un constructeur de `T`.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type `T` est constructible de façon triviale en utilisant les types d’arguments dans `Args`. Sinon, sa valeur est false. Le type `T` est constructible de façon triviale si la définition de variable `T t(std::declval<Args>()...);` est bien formée et est connue pour n’appeler aucune opération non triviale. `T` et tous les types dans `Args` doivent être des types complets, `void`, ou des tableaux de limite inconnue.

## <a name="requirements"></a>Spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
