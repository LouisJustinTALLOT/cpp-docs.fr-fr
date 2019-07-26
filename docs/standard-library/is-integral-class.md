---
title: is_integral, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_integral
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
ms.openlocfilehash: a367bb06f49dd2c9c64f0c257a3573add5645efe
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456236"
---
# <a name="isintegral-class"></a>is_integral, classe

Teste si le type est intégral.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_integral;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *Ty* est l’un des types intégraux ou `cv-qualified` une forme de l’un des types intégraux. sinon, sa valeur est false.

Un type intégral est l’un des types **bool**, **char**, unsigned **char**, signed **char**, **wchar_t**, **short**, unsigned **short**, **int**, unsigned **int**, **long**et unsigned **long**. En outre, avec les compilateurs qui les fournissent, un type intégral peut être **un de long**long, unsigned **long long**, **_** _ Int64 et unsigned _ _ Int64.

## <a name="example"></a>Exemples

```cpp
// std__type_traits__is_integral.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_integral<trivial> == " << std::boolalpha
        << std::is_integral<trivial>::value << std::endl;
    std::cout << "is_integral<int> == " << std::boolalpha
        << std::is_integral<int>::value << std::endl;
    std::cout << "is_integral<float> == " << std::boolalpha
        << std::is_integral<float>::value << std::endl;

    return (0);
    }
```

```Output
is_integral<trivial> == false
is_integral<int> == true
is_integral<float> == false
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[is_enum, classe](../standard-library/is-enum-class.md)\
[is_floating_point, classe](../standard-library/is-floating-point-class.md)
