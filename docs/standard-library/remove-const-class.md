---
title: remove_const, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_const
helpviewer_keywords:
- remove_const class
- remove_const
ms.assetid: feb76fb3-9228-41d6-80f6-2fbb04daec43
ms.openlocfilehash: 0091c77d33e1fcd2be5b361680c9422210866be2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451355"
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

*T*\
Type à modifier.

## <a name="remarks"></a>Notes

Une instance de `remove_const<T>` contient un type modifié qui est `T1` quand *t* se présente sous la forme `const T1`, sinon *t*.

## <a name="example"></a>Exemples

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

[<type_traits>](../standard-library/type-traits.md)\
[add_const, classe](../standard-library/add-const-class.md)\
[remove_cv, classe](../standard-library/remove-cv-class.md)
