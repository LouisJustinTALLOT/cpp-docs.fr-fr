---
title: is_convertible, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_convertible
dev_langs:
- C++
helpviewer_keywords:
- is_convertible class
- is_convertible
ms.assetid: 75614008-1894-42ea-bd57-974399628536
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52a062d29124cd5ba4c0008c554d72f59aa8c645
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110537"
---
# <a name="isconvertible-class"></a>is_convertible, classe

Teste si un type est convertible en un autre.

## <a name="syntax"></a>Syntaxe

```cpp
template <class From, class To>
struct is_convertible;
```

### <a name="parameters"></a>Paramètres

*From*<br/>
Type à partir duquel effectuer la conversion.

*Ty*<br/>
Type vers lequel effectuer la conversion.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si l'expression `To to = from;`, où `from` est un objet de type `From`, est formée correctement.

## <a name="example"></a>Exemple

```cpp
// std__type_traits__is_convertible.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_convertible<trivial, int> == " << std::boolalpha
        << std::is_convertible<trivial, int>::value << std::endl;
    std::cout << "is_convertible<trivial, trivial> == " << std::boolalpha
        << std::is_convertible<trivial, trivial>::value << std::endl;
    std::cout << "is_convertible<char, int> == " << std::boolalpha
        << std::is_convertible<char, int>::value << std::endl;

    return (0);
    }

```

```Output
is_convertible<trivial, int> == false
is_convertible<trivial, trivial> == true
is_convertible<char, int> == true
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_base_of, classe](../standard-library/is-base-of-class.md)<br/>
