---
title: remove_const, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_const
helpviewer_keywords:
- remove_const class
- remove_const
ms.assetid: feb76fb3-9228-41d6-80f6-2fbb04daec43
ms.openlocfilehash: 04f7c6475d88f843ef381563f80559529e6b59e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477179"
---
# <a name="removeconst-class"></a>remove_const, classe

Crée un type non const à partir d'un type.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct remove_const;
```

```cpp
template <class T>
using remove_const_t = typename remove_const<T>::type;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Type à modifier.

## <a name="remarks"></a>Notes

Une instance de `remove_const<T>` contient un type modifié qui est `T1` lorsque *T* est au format `const T1`, sinon *T*.

## <a name="example"></a>Exemple

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    int *p = (std::remove_const_t<const int>*)0;

    p = p;  // to quiet "unused" warning
    std::cout << "remove_const_t<const int> == "
        << typeid(*p).name() << std::endl;

    return (0);
    }
```

```Output
remove_const_t<const int> == int
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[add_const, classe](../standard-library/add-const-class.md)<br/>
[remove_cv, classe](../standard-library/remove-cv-class.md)<br/>
