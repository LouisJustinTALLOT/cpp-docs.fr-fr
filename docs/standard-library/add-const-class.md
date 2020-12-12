---
description: 'En savoir plus sur : classe add_const'
title: add_const, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_const
helpviewer_keywords:
- add_const class
- add_const
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
ms.openlocfilehash: ce1dd895a5968234feca7905d3b9f8d571336053
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319942"
---
# <a name="add_const-class"></a>add_const, classe

Crée un type const à partir d'un type.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct add_const;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à modifier.

## <a name="remarks"></a>Notes

Une instance du modificateur de type contient un type modifié qui est *Ty* si *Ty* est une référence, une fonction ou un type qualifié const ; sinon, `const Ty` .

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

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](type-traits.md)\
[Classe remove_const](remove-const-class.md)
