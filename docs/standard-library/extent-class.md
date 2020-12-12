---
description: 'En savoir plus sur : classe d’étendue'
title: extent, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::extent
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
ms.openlocfilehash: d3db49db99d2cb7a241ca3b69c48fa6bcf2cb490
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324384"
---
# <a name="extent-class"></a>extent, classe

Obtient une dimension de tableau.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

*Cliqu*\
Tableau lié à interroger.

## <a name="remarks"></a>Notes

Si *Ty* est un type tableau qui possède au moins *I* dimensions, la requête de type contient le nombre d’éléments dans la dimension spécifiée par *I*. Si *Ty* n’est pas un type tableau ou si son rang est inférieur à *i*, ou si *i* est égal à zéro et que *Ty* est de type « tableau de limite inconnue de `U` », la requête de type contient la valeur 0.

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

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[Classe remove_all_extents](../standard-library/remove-all-extents-class.md)\
[Classe remove_extent](../standard-library/remove-extent-class.md)
