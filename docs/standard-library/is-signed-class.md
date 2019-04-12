---
title: is_signed, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_signed
helpviewer_keywords:
- is_signed class
- is_signed
ms.assetid: 20ae44d9-22ad-4fbd-b26a-f18c62689451
ms.openlocfilehash: eacc271697930bec64630c0a1be612bd89eeb91f
ms.sourcegitcommit: 88631cecbe3e3fa752eae3ad05b7f9d9f9437b4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59534134"
---
# <a name="issigned-class"></a>is_signed, classe

Tester si le type est entier signé.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_signed;
```

### <a name="parameters"></a>Paramètres

*Ty*<br/>
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *Ty* est un type intégral signé ou un `cv-qualified` un type intégral signé, sinon, sa valeur est false.

## <a name="example"></a>Exemple

```cpp
// std__type_traits__is_signed.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_signed<trivial> == " << std::boolalpha
        << std::is_signed<trivial>::value << std::endl;
    std::cout << "is_signed<int> == " << std::boolalpha
        << std::is_signed<int>::value << std::endl;
    std::cout << "is_signed<unsigned int> == " << std::boolalpha
        << std::is_signed<unsigned int>::value << std::endl;
    std::cout << "is_signed<float> == " << std::boolalpha
        << std::is_signed<float>::value << std::endl;

    return (0);
    }
```

```Output
is_signed<trivial> == false
is_signed<int> == true
is_signed<unsigned int> == false
is_signed<float> == true
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_unsigned, classe](../standard-library/is-unsigned-class.md)<br/>
