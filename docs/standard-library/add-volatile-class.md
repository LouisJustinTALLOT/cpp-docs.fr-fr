---
title: add_volatile, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_volatile
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
ms.openlocfilehash: ff48b1848e2d7631d789621a5ef845d04d8e8821
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495938"
---
# <a name="addvolatile-class"></a>add_volatile, classe

Rend un **volatile** type à partir du type spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct add_volatile;

template <class T>
using add_volatile_t = typename add_volatile<T>::type;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type à modifier.

## <a name="remarks"></a>Notes

Une instance de `add_volatile<T>` a un membre **typedef** `type` c'est-à-dire *T* si *T* est une référence, une fonction ou un type qualifié volatile, sinon **volatile** *T*. L’alias `add_volatile_t` est un raccourci pour accéder au membre **typedef** `type`.

## <a name="example"></a>Exemple

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_volatile_t<int> *p = (volatile int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_volatile<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_volatile<int> == int
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_volatile, classe](../standard-library/remove-volatile-class.md)<br/>
