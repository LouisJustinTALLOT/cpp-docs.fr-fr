---
description: 'En savoir plus sur : classe is_compound'
title: is_compound, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_compound
helpviewer_keywords:
- is_compound class
- is_compound
ms.assetid: bdad1167-cf3f-4f37-8321-62a5df159ead
ms.openlocfilehash: 0bdd1b2f8c7ab827d9bed1025e30140244381c3a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323828"
---
# <a name="is_compound-class"></a>is_compound, classe

Teste si le type spécifié n'est pas fondamental.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_compound;
```

### <a name="parameters"></a>Paramètres

*Ty*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type contient **`false`** si le type de *Ty* est un type fondamental (autrement dit, si [is_fundamental](../standard-library/is-fundamental-class.md) \<Ty> contient **`true`** ); sinon, il contient **`true`** . Ainsi, le prédicat contient **`true`** si *Ty* est un type tableau, un type de fonction, un pointeur vers **`void`** ou un objet ou une fonction, une référence, une classe, une Union, une énumération ou un pointeur vers un membre de classe non statique, ou une forme *CV-Qualified* de l’un d’eux.

## <a name="example"></a>Exemple

```cpp
// std__type_traits__is_compound.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_compound<trivial> == " << std::boolalpha
        << std::is_compound<trivial>::value << std::endl;
    std::cout << "is_compound<int[]> == " << std::boolalpha
        << std::is_compound<int[]>::value << std::endl;
    std::cout << "is_compound<int()> == " << std::boolalpha
        << std::is_compound<int()>::value << std::endl;
    std::cout << "is_compound<int&> == " << std::boolalpha
        << std::is_compound<int&>::value << std::endl;
    std::cout << "is_compound<void *> == " << std::boolalpha
        << std::is_compound<void *>::value << std::endl;
    std::cout << "is_compound<int> == " << std::boolalpha
        << std::is_compound<int>::value << std::endl;

    return (0);
    }
```

```Output
is_compound<trivial> == true
is_compound<int[]> == true
is_compound<int()> == true
is_compound<int&> == true
is_compound<void *> == true
is_compound<int> == false
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[Classe is_class](../standard-library/is-class-class.md)
