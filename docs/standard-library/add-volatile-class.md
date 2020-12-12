---
description: 'En savoir plus sur : classe add_volatile'
title: add_volatile, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_volatile
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
ms.openlocfilehash: 6f138c9009d127efe2d640124d9af1e114eb0732
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319867"
---
# <a name="add_volatile-class"></a>add_volatile, classe

Crée un **`volatile`** type à partir du type spécifié.

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

Une instance de `add_volatile<T>` a un membre **`typedef`** `type` qui est *t* si *t* est une référence, une fonction ou un type qualifié volatile, sinon **`volatile`** *t*. L’alias `add_volatile_t` est un raccourci pour accéder au membre **`typedef`** `type` .

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

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](type-traits.md)\
[Classe remove_volatile](remove-volatile-class.md)
