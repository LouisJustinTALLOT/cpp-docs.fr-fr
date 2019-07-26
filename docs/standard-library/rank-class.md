---
title: rank, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::rank
helpviewer_keywords:
- rank class
- rank
ms.assetid: bc9f1b8f-800f-46ca-b6f4-d8579ed5406a
ms.openlocfilehash: cab8d4bb782c7e02df62874a40db14479558da99
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458179"
---
# <a name="rank-class"></a>rank, classe

Obtient le nombre de dimensions de tableau.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct rank;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

## <a name="remarks"></a>Notes

La requête de type contient la valeur du nombre de dimensions du type de tableau *Ty*, ou 0 si *Ty* n’est pas un type tableau.

## <a name="example"></a>Exemple

```cpp
// std__type_traits__rank.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "rank<int> == "
        << std::rank<int>::value << std::endl;
    std::cout << "rank<int[5]> == "
        << std::rank<int[5]>::value << std::endl;
    std::cout << "rank<int[5][10]> == "
        << std::rank<int[5][10]>::value << std::endl;

    return (0);
    }
```

```Output
rank<int> == 0
rank<int[5]> == 1
rank<int[5][10]> == 2
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[extent, classe](../standard-library/extent-class.md)
