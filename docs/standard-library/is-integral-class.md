---
description: 'En savoir plus sur : classe is_integral'
title: is_integral, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_integral
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
ms.openlocfilehash: db586054614b9a5ef49ffe9fe8b643b35c65a217
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323699"
---
# <a name="is_integral-class"></a>is_integral, classe

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

Une instance du prédicat de type a la valeur true si le type *Ty* est l’un des types intégraux ou une `cv-qualified` forme de l’un des types intégraux. sinon, sa valeur est false.

Un type intégral est un de **`bool`** , **`char`** , **`unsigned char`** , **`signed char`** ,,,,,, **`wchar_t`** **`short`** **`unsigned short`** **`int`** **`unsigned int`** **`long`** et **`unsigned long`** . En outre, avec les compilateurs qui les fournissent, un type intégral peut être,, **`long long`** **`unsigned long long`** **`__int64`** et **non signé __int64**.

## <a name="example"></a>Exemple

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

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[Classe is_enum](../standard-library/is-enum-class.md)\
[Classe is_floating_point](../standard-library/is-floating-point-class.md)
