---
title: remove_volatile, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_volatile
helpviewer_keywords:
- remove_volatile class
- remove_volatile
ms.assetid: 8b87e2c2-a581-4eb3-8691-c5603910d61d
ms.openlocfilehash: 19514d1839fa6e0afcecb690dcb12657a85f3c2e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451261"
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

*T*\
Type à modifier.

## <a name="remarks"></a>Notes

Une instance de `remove_volatile<T>` contient un type modifié qui est `T1` quand *t* se présente sous la forme `volatile T1`, sinon *t*.

## <a name="example"></a>Exemples

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

[<type_traits>](../standard-library/type-traits.md)\
[add_volatile, classe](../standard-library/add-volatile-class.md)
