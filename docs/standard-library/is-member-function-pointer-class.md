---
title: is_member_function_pointer, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_member_function_pointer
dev_langs:
- C++
helpviewer_keywords:
- is_member_function_pointer class
- is_member_function_pointer
ms.assetid: 02e372c4-2714-40f2-b376-2e10ca91c8ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c8f72191a84661749db87958a2c08807c00d446
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845035"
---
# <a name="ismemberfunctionpointer-class"></a>is_member_function_pointer, classe

Teste si le type est un pointeur vers une fonction membre.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_member_function_pointer;
```

### <a name="parameters"></a>Paramètres

`Ty` Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type `Ty` est un pointeur vers une fonction membre ou un pointeur `cv-qualified` vers une fonction membre. Sinon, sa valeur est false.

## <a name="example"></a>Exemple

```cpp
// std__type_traits__is_member_function_pointer.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

struct functional
    {
    int f();
    };

int main()
    {
    std::cout << "is_member_function_pointer<trivial *> == "
        << std::boolalpha
        << std::is_member_function_pointer<trivial *>::value
        << std::endl;
    std::cout << "is_member_function_pointer<int trivial::*> == "
        << std::boolalpha
        << std::is_member_function_pointer<int trivial::*>::value
        << std::endl;
    std::cout << "is_member_function_pointer<int (functional::*)()> == "
        << std::boolalpha
        << std::is_member_function_pointer<int (functional::*)()>::value
        << std::endl;

    return (0);
    }

```

```Output
is_member_function_pointer<trivial *> == false
is_member_function_pointer<int trivial::*> == false
is_member_function_pointer<int (functional::*)()> == true
```

## <a name="requirements"></a>Spécifications

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_member_pointer, classe](../standard-library/is-member-pointer-class.md)<br/>
