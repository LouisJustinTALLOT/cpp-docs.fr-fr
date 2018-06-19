---
title: is_nothrow_constructible, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 112da495673517f86a00437672ccc52429fbd251
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842740"
---
# <a name="isnothrowconstructible-class"></a>is_nothrow_constructible, classe

Teste si un type est constructible et est connu comme ne levant pas d’exception quand les types d’arguments spécifiés sont utilisés.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>Paramètres

`T` Type à interroger.

`Args` Les types d’arguments à faire correspondre dans un constructeur de `T`.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type `T` est constructible à l’aide des types d’arguments dans `Args`, et que le constructeur est connu par le compilateur comme ne levant pas d’exception. Sinon, sa valeur est false. Le type `T` est constructible si la définition de variable `T t(std::declval<Args>()...);` est bien formée. `T` et tous les types dans `Args` doivent être des types complets, `void`, ou des tableaux de limite inconnue.

## <a name="requirements"></a>Spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
