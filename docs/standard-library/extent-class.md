---
title: extent, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::extent
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
ms.openlocfilehash: 716f4fcd90e97eaeb3f56c8429379590d176e1c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428143"
---
# <a name="extent-class"></a>extent, classe

Obtient une dimension de tableau.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>Paramètres

*Ty*<br/>
Type à interroger.

*I*<br/>
Tableau lié à interroger.

## <a name="remarks"></a>Notes

Si *Ty* est un type de tableau qui possède au moins *je* dimensions, la requête de type contient le nombre d’éléments dans la dimension spécifiée par *je*. Si *Ty* n’est pas un type tableau ou son rang est inférieur à *je*, ou si *je* est égal à zéro et *Ty* est de type « tableau inconnu lié de `U` «, la requête de type conserve la valeur 0.

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

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_all_extents, classe](../standard-library/remove-all-extents-class.md)<br/>
[remove_extent, classe](../standard-library/remove-extent-class.md)<br/>
