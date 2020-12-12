---
description: 'En savoir plus sur : classe is_same'
title: is_same, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_same
helpviewer_keywords:
- is_same class
- is_same
ms.assetid: d9df6c1d-c270-4ec2-802a-af275648dd1d
ms.openlocfilehash: 19e0ecec009227c0785c263893aa32beff4049e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247720"
---
# <a name="is_same-class"></a>is_same, classe

Teste si deux types sont identiques.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty1, class Ty2>
struct is_same;
```

### <a name="parameters"></a>Paramètres

*Ty1*\
Premier type à interroger.

*Ty2*\
Deuxième type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si les types *Ty1* et *Ty2* sont du même type. sinon, sa valeur est false.

## <a name="example"></a>Exemple

```cpp
// std__type_traits__is_same.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct base
    {
    int val;
    };

struct derived
    : public base
    {
    };

int main()
    {
    std::cout << "is_same<base, base> == " << std::boolalpha
        << std::is_same<base, base>::value << std::endl;
    std::cout << "is_same<base, derived> == " << std::boolalpha
        << std::is_same<base, derived>::value << std::endl;
    std::cout << "is_same<derived, base> == " << std::boolalpha
        << std::is_same<derived, base>::value << std::endl;
    std::cout << "is_same<int, int> == " << std::boolalpha
        << std::is_same<int, int>::value << std::endl;
    std::cout << "is_same<int, const int> == " << std::boolalpha
        << std::is_same<int, const int>::value << std::endl;

    return (0);
    }
```

```Output
is_same<base, base> == true
is_same<base, derived> == false
is_same<derived, base> == false
is_same<int, int> == true
is_same<int, const int> == false
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[Classe is_convertible](../standard-library/is-convertible-class.md)\
[Classe is_base_of](../standard-library/is-base-of-class.md)
