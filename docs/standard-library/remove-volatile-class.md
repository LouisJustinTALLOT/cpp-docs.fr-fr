---
title: remove_volatile, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_volatile
helpviewer_keywords:
- remove_volatile class
- remove_volatile
ms.assetid: 8b87e2c2-a581-4eb3-8691-c5603910d61d
ms.openlocfilehash: b327bb8362e1f6523d22950974012747e0de99f8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442001"
---
# <a name="removevolatile-class"></a>remove_volatile, classe

Rend un type non volatile.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct remove_volatile;

template <class T>
using remove_volatile_t = typename remove_volatile<T>::type;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type à modifier.

## <a name="remarks"></a>Notes

Une instance de `remove_volatile<T>` contient un type modifié qui est `T1` lorsque *T* est au format `volatile T1`, sinon *T*.

## <a name="example"></a>Exemple

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    int *p = (std::remove_volatile_t<volatile int> *)0;

    p = p;  // to quiet "unused" warning
    std::cout << " remove_volatile_t<volatile int> == "
        << typeid(*p).name() << std::endl;

    return (0);
    }
```

```Output
remove_volatile_t<volatile int> == int
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[add_volatile, classe](../standard-library/add-volatile-class.md)<br/>
