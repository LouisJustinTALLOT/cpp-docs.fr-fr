---
description: 'En savoir plus sur : classe is_default_constructible'
title: is_default_constructible, classe
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_default_constructible
helpviewer_keywords:
- is_default_constructible
ms.assetid: dd8f1c44-dae5-4258-891f-c5e048d94092
ms.openlocfilehash: 9c5365ee6e2e2b7382b5dd5f17cce2afd0ce8932
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323780"
---
# <a name="is_default_constructible-class"></a>is_default_constructible, classe

Teste si un type a un constructeur par défaut.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>Paramètres

*T*\
Type à interroger.

## <a name="remarks"></a>Notes

Une instance du prédicat de type a la valeur true si le type *T* est un type de classe qui a un constructeur par défaut. sinon, sa valeur est false. Cela est équivalent au prédicat `is_constructible<T>`. Le type *T* doit être un type complet, **`void`** , ou un tableau de limite inconnue.

## <a name="example"></a>Exemple

```cpp
#include <type_traits>
#include <iostream>

struct Simple
{
    Simple() : val(0) {}
    int val;
};

struct Simple2
{
    Simple2(int v) : val(v) {}
    int val;
};

int main()
{
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha
        << std::is_default_constructible<Simple>::value << std::endl;
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha
        << std::is_default_constructible<Simple2>::value << std::endl;

    return (0);
}
```

```Output
is_default_constructible<Simple> == true
is_default_constructible<Simple2> == false
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)
