---
title: remove_reference, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_reference
helpviewer_keywords:
- remove_reference class
- remove_reference
ms.assetid: 294e1965-3ae3-46ee-bc42-4fdf60c24717
ms.openlocfilehash: f185994f943b2419a67fe86ce957751dc4031cbe
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451271"
---
# <a name="removereference-class"></a>remove_reference, classe

Convertit un type en un type autre qu'un type référence.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct remove_reference;

template <class T>
using remove_reference_t = typename remove_reference<T>::type;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à modifier.

## <a name="remarks"></a>Notes

Une instance de `remove_reference<T>` contient un type modifié qui est `T1` quand *t* se présente sous la forme `T1&`, sinon *t*.

## <a name="example"></a>Exemple

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    int *p = (std::remove_reference_t<int&> *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "remove_reference_t<int&> == "
        << typeid(*p).name() << std::endl;

    return (0);
    }
```

```Output
remove_reference_t<int&> == int
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[add_lvalue_reference, classe](../standard-library/add-lvalue-reference-class.md)
