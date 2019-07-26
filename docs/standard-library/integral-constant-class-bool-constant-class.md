---
title: integral_constant, classe, bool_constant, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
helpviewer_keywords:
- std::integral_constant [C++]
- std::bool_constant [C++]
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
ms.openlocfilehash: c85da1f3be7821f8d82cd2b19dab2a5864426a5a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452043"
---
# <a name="integralconstant-class-boolconstant-class"></a>integral_constant, classe, bool_constant, classe

Crée une constante intégrale à partir d’un type et d’une valeur.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T, T v>
struct integral_constant {
   static constexpr T value = v;
   typedef T value_type;
   typedef integral_constant<T, v> type;
   constexpr operator value_type() const noexcept;
   constexpr value_type operator()() const noexcept;
   };
```

### <a name="parameters"></a>Paramètres

*T*\
Type de la constante.

*v*\
Valeur de la constante.

## <a name="remarks"></a>Notes

La classe de modèle `integral_constant`, quand elle est spécialisée avec un type intégral *T* et une valeur *v* de ce type, représente un objet qui contient une constante de ce type intégral avec la valeur spécifiée. Le membre nommé `type` est un alias pour le type de spécialisation de modèle généré, et le membre `value` contient la valeur *v* servant à créer la spécialisation.

La `bool_constant` classe de modèle est une spécialisation partielle `integral_constant` explicite de qui utilise **bool** comme argument *T* .

## <a name="example"></a>Exemple

```cpp
// std__type_traits__integral_constant.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "integral_constant<int, 5> == "
        << std::integral_constant<int, 5>::value << std::endl;
    std::cout << "integral_constant<bool, false> == " << std::boolalpha
        << std::integral_constant<bool, false>::value << std::endl;

    return (0);
    }
```

```Output
integral_constant<int, 5> == 5
integral_constant<bool, false> == false
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[false_type](../standard-library/type-traits-typedefs.md#false_type)\
[true_type](../standard-library/type-traits-typedefs.md#true_type)
