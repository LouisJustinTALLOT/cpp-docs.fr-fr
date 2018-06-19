---
title: extent, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::extent
dev_langs:
- C++
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7fb721b23f473c59051e72edc969e5de38f1c984
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843247"
---
# <a name="extent-class"></a>extent, classe

Obtient une dimension de tableau.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>Paramètres

`Ty` Type à interroger.

`I` Le tableau lié à interroger.

## <a name="remarks"></a>Notes

Si `Ty` est un type tableau qui possède au moins `I` dimensions, la requête de type contient le nombre d'éléments dans la dimension spécifié par `I`. Si `Ty` n'est pas un type tableau ou si son rang est inférieur à `I`, ou si `I` est égal à zéro et que `Ty` est de type « tableau ayant des limites d'index inconnues de `U` », la requête de type contient la valeur 0.

## <a name="example"></a>Exemple

```cpp
// std__type_traits__extent.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "extent 0 == "
        << std::extent<int[5][10]>::value << std::endl;
    std::cout << "extent 1 == "
        << std::extent<int[5][10], 1>::value << std::endl;

    return (0);
    }

```

```Output
extent 0 == 5
extent 1 == 10
```

## <a name="requirements"></a>Spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_all_extents, classe](../standard-library/remove-all-extents-class.md)<br/>
[remove_extent, classe](../standard-library/remove-extent-class.md)<br/>
