---
title: is_compound, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_compound
dev_langs:
- C++
helpviewer_keywords:
- is_compound class
- is_compound
ms.assetid: bdad1167-cf3f-4f37-8321-62a5df159ead
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d062912a441f16e9eb26415287fbbb574b829e9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843806"
---
# <a name="iscompound-class"></a>is_compound, classe

Teste si le type spécifié n'est pas fondamental.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_compound;
```

### <a name="parameters"></a>Paramètres

`Ty` Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a `false` si le type de `Ty` est un type fondamental (autrement dit, si [is_fundamental](../standard-library/is-fundamental-class.md)\<Ty > contient `true`) ; sinon, il conserve `true`. Ainsi, le prédicat a la valeur `true` si `Ty` est un type tableau, un type fonction, un pointeur vers `void` ou un objet ou une fonction, une référence, une classe, une union, une énumération ou un pointeur vers un membre de classe non statique, ou une forme *cv-qualified* de l’un d’eux.

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

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_class, classe](../standard-library/is-class-class.md)<br/>
