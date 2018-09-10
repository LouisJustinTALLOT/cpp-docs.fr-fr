---
title: is_base_of, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_base_of
dev_langs:
- C++
helpviewer_keywords:
- is_base_of class
- is_base_of
ms.assetid: 436f6213-1d4c-4ffc-a588-fc7c4887dd86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6085624ca80fa676da89e10686b84323e1a7db89
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110277"
---
# <a name="isbaseof-class"></a>is_base_of, classe

Teste si un type est la base d'un autre.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Base, class Derived>
struct is_base_of;
```

### <a name="parameters"></a>Paramètres

*base de*<br/>
Classe de base à tester.

*DÉRIVÉS*<br/>
Type dérivé à tester.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *Base* est une classe de base du type *dérivé*, sinon, sa valeur est false.

## <a name="example"></a>Exemple

```cpp
#include <type_traits>
#include <iostream>

struct base
    {
    int val;
    };

struct derived
    : public base
    {
    };

int main()
    {
    std::cout << "is_base_of<base, base> == " << std::boolalpha
        << std::is_base_of<base, base>::value << std::endl;
    std::cout << "is_base_of<base, derived> == " << std::boolalpha
        << std::is_base_of<base, derived>::value << std::endl;
    std::cout << "is_base_of<derived, base> == " << std::boolalpha
        << std::is_base_of<derived, base>::value << std::endl;

    return (0);
    }
```

```Output
is_base_of<base, base> == true
is_base_of<base, derived> == true
is_base_of<derived, base> == false
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_convertible, classe](../standard-library/is-convertible-class.md)<br/>
