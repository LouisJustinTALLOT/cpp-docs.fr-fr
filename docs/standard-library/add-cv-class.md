---
description: 'En savoir plus sur : classe add_cv'
title: add_cv, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_cv
helpviewer_keywords:
- add_cv class
- add_cv
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
ms.openlocfilehash: bc25efd879a27b3d3af2e5f4db8dd74fafa3fb45
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319929"
---
# <a name="add_cv-class"></a>add_cv, classe

Crée un **`const volatile`** type à partir d’un type.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct add_cv;

template <class T>
using add_cv_t = typename add_cv<T>::type;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à modifier.

## <a name="remarks"></a>Notes

Une instance du type modifié `add_cv<T>` a un `type` membre **`typedef`** équivalant à *T* modifié par [Add_volatile](add-volatile-class.md) et [add_const](add-const-class.md), sauf si *T* a déjà les qualificateurs CV, est une référence ou est une fonction.

Le type d’assistance `add_cv_t<T>` est un raccourci pour accéder au typedef de membre de `add_cv<T>``type`.

## <a name="example"></a>Exemple

```cpp
// add_cv.cpp
// compile by using: cl /EHsc /W4 add_cv.cpp
#include <type_traits>
#include <iostream>

struct S {
    void f() {
        std::cout << "invoked non-cv-qualified S.f()" << std::endl;
    }
    void f() const {
        std::cout << "invoked const S.f()" << std::endl;
    }
    void f() volatile {
        std::cout << "invoked volatile S.f()" << std::endl;
    }
    void f() const volatile {
        std::cout << "invoked const volatile S.f()" << std::endl;
    }
};

template <class T>
void invoke() {
    T t;
    ((T *)&t)->f();
}

int main()
{
    invoke<S>();
    invoke<std::add_const<S>::type>();
    invoke<std::add_volatile<S>::type>();
    invoke<std::add_cv<S>::type>();
}
```

```Output
invoked non-cv-qualified S.f()
invoked const S.f()
invoked volatile S.f()
invoked const volatile S.f()
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](type-traits.md)\
[Classe remove_const](remove-const-class.md)\
[Classe remove_volatile](remove-volatile-class.md)
