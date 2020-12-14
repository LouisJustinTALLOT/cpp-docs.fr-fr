---
description: 'En savoir plus sur : classe is_base_of'
title: is_base_of, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_base_of
helpviewer_keywords:
- is_base_of class
- is_base_of
ms.assetid: 436f6213-1d4c-4ffc-a588-fc7c4887dd86
ms.openlocfilehash: 6cb2b55a6df687fbb7da74ca3c696a8a9b0ffbad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231262"
---
# <a name="is_base_of-class"></a>is_base_of, classe

Teste si un type est la base d'un autre.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Base, class Derived>
struct is_base_of;
```

### <a name="parameters"></a>Paramètres

*Base*\
Classe de base à tester.

*Issue*\
Type dérivé à tester.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type de *base* est une classe de base du type *dérivé*. sinon, sa valeur est false.

## <a name="example"></a>Exemple

```cpp
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
    std::cout << "is_base_of<base, base> == " << std::boolalpha
        << std::is_base_of<base, base>::value << std::endl;
    std::cout << "is_base_of<base, derived> == " << std::boolalpha
        << std::is_base_of<base, derived>::value << std::endl;
    std::cout << "is_base_of<derived, base> == " << std::boolalpha
        << std::is_base_of<derived, base>::value << std::endl;

    return (0);
    }
```

```Output
is_base_of<base, base> == true
is_base_of<base, derived> == true
is_base_of<derived, base> == false
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[Classe is_convertible](../standard-library/is-convertible-class.md)
