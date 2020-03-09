---
title: '&lt;type_traits&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::false_type
- xtr1common/std::false_type
- type_traits/std::true_type
- xtr1common/std::true_type
ms.assetid: 8ac040ca-ed2d-4570-adc9-cb5626530053
ms.openlocfilehash: eff1a99fb95f15c6377e8a74cca36e718cbd6fd9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867216"
---
# <a name="lttype_traitsgt-typedefs"></a>&lt;type_traits&gt;, typedefs

|||
|-|-|
|[false_type](#false_type)|[true_type](#true_type)|

## <a name="false_type"></a>  false_type, typedef

Contient une constante intégrale avec la valeur false.

```cpp
typedef integral_constant<bool, false> false_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme pour une spécialisation du modèle `integral_constant`.

### <a name="example"></a>Exemple

```cpp
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="true_type"></a>  true_type, typedef

Contient une constante intégrale avec la valeur true.

```cpp
typedef integral_constant<bool, true> true_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme pour une spécialisation du modèle `integral_constant`.

### <a name="example"></a>Exemple

```cpp
// std__type_traits__true_type.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
