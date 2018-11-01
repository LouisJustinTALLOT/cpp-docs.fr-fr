---
title: add_const, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_const
helpviewer_keywords:
- add_const class
- add_const
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
ms.openlocfilehash: dc457fd4efba538e96200f7f42f84a73fc1b5228
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438648"
---
# <a name="addconst-class"></a>add_const, classe

Crée un type const à partir d'un type.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct add_const;
```

### <a name="parameters"></a>Paramètres

*Ty*<br/>
Type à modifier.

## <a name="remarks"></a>Notes

Une instance du modificateur de type conserve un type modifié qui est *Ty* si *Ty* est une référence, une fonction ou un type qualifié const, sinon `const Ty`.

## <a name="example"></a>Exemple

```cpp
// std__type_traits__add_const.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
{
    std::add_const<int>::type *p = (const int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_const<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_const<int> == int
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_const, classe](../standard-library/remove-const-class.md)<br/>
