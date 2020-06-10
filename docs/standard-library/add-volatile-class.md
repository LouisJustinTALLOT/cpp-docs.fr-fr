---
title: add_volatile, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_volatile
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
ms.openlocfilehash: 1a4ad8a86b88cdfa98f043bb49ba6eeff8b090c9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619204"
---
# <a name="add_volatile-class"></a>add_volatile, classe

Crée un type **volatile** à partir du type spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct add_volatile;

template <class T>
using add_volatile_t = typename add_volatile<T>::type;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à modifier.

## <a name="remarks"></a>Notes

Une instance de `add_volatile<T>` a un **typedef** de membre `type` qui est *t* si *t* est une référence, une fonction ou un type qualifié volatile, sinon **volatile** *T*. L’alias `add_volatile_t` est un raccourci pour accéder au **typedef** de membre `type` .

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

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](type-traits.md)\
[Classe remove_volatile](remove-volatile-class.md)
