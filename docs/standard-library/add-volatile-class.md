---
title: add_volatile, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_volatile
dev_langs:
- C++
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8775c681954799e2239da5ad429f9f8131ca25b1
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958888"
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

*T* type à modifier.

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
