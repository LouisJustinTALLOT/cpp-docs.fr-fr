---
description: 'En savoir plus sur : classe is_unsigned'
title: is_unsigned, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_unsigned
helpviewer_keywords:
- is_unsigned class
- is_unsigned
ms.assetid: ba5bec3d-796b-4e54-8595-a3941ec6a8dc
ms.openlocfilehash: 2ad1aff24d578c2073aa649fb78b73d28ab1a6cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197203"
---
# <a name="is_unsigned-class"></a>is_unsigned, classe

Teste si le type est un entier non signé.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_unsigned;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *Ty* est un type intégral non signé ou un `cv-qualified` type intégral non signé. sinon, sa valeur est false.

## <a name="example"></a>Exemple

```cpp
// std__type_traits__is_unsigned.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_unsigned<trivial> == " << std::boolalpha
        << std::is_unsigned<trivial>::value << std::endl;
    std::cout << "is_unsigned<int> == " << std::boolalpha
        << std::is_unsigned<int>::value << std::endl;
    std::cout << "is_unsigned<unsigned int> == " << std::boolalpha
        << std::is_unsigned<unsigned int>::value << std::endl;
    std::cout << "is_unsigned<float> == " << std::boolalpha
        << std::is_unsigned<float>::value << std::endl;

    return (0);
    }
```

```Output
is_unsigned<trivial> == false
is_unsigned<int> == false
is_unsigned<unsigned int> == true
is_unsigned<float> == false
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[Classe is_signed](../standard-library/is-signed-class.md)
