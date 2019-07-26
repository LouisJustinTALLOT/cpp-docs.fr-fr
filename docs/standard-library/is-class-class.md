---
title: is_class, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_class
helpviewer_keywords:
- is_class class
- is_class
ms.assetid: 96fc34a3-a81b-4ec6-b7fb-baafde1a0f4e
ms.openlocfilehash: 7dc71622a37164e996b067276ddf8a5d1dd88b62
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456651"
---
# <a name="isclass-class"></a>is_class, classe

Teste si le type est une classe.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_class;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *Ty* est un type défini comme une **classe** ou un **struct**, ou `cv-qualified` une forme de l’un d’eux. sinon, sa valeur est false.

## <a name="example"></a>Exemples

```cpp
// std__type_traits__is_class.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_class<trivial> == " << std::boolalpha
        << std::is_class<trivial>::value << std::endl;
    std::cout << "is_class<int> == " << std::boolalpha
        << std::is_class<int>::value << std::endl;

    return (0);
    }
```

```Output
is_class<trivial> == true
is_class<int> == false
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[is_compound, classe](../standard-library/is-compound-class.md)\
[is_union, classe](../standard-library/is-union-class.md)
