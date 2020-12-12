---
description: 'En savoir plus sur les classes suivantes : is_invocable, is_invocable_r, is_nothrow_invocable, is_nothrow_invocable_r'
title: classes is_invocable, is_invocable_r, is_nothrow_invocable, is_nothrow_invocable_r
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::is_invocable
- type_traits/std::is_invocable_r
- type_traits/std::is_nothrow_invocable
- type_traits/std::is_nothrow_invocable_r
helpviewer_keywords:
- is_invocable class
- is_invocable
- is_invocable_r class
- is_invocable_r
- is_nothrow_invocable class
- is_nothrow_invocable
- is_nothrow_invocable_r class
- is_nothrow_invocable_r
ms.openlocfilehash: 117e2ff85634898e170223e726a2cfea0ac6a470
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230929"
---
# <a name="is_invocable-is_invocable_r-is_nothrow_invocable-is_nothrow_invocable_r-classes"></a>classes is_invocable, is_invocable_r, is_nothrow_invocable, is_nothrow_invocable_r

Ces modèles déterminent si un type peut être appelé avec les types d’arguments spécifiés. `is_invocable_r` et `is_nothrow_invocable_r` déterminent également si le résultat de l’appel est convertible en un type spécifique. `is_nothrow_invocable` et `is_nothrow_invocable_r` déterminent également si l’appel est connu pour ne pas lever d’exceptions. Ajouté en C++ 17.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Callable, class... Args>
struct is_invocable;

template <class Convertible, class Callable, class... Args>
struct is_invocable_r;

template <class Callable, class... Args>
struct is_nothrow_invocable;

template <class Convertible, class Callable, class... Args>
struct is_nothrow_invocable_r;

// Helper templates
template <class Callable, class... Args>
inline constexpr bool is_invocable_v =
    std::is_invocable<Callable, Args...>::value;

template <class Convertible, class Callable, class... Args>
inline constexpr bool is_invocable_r_v =
    std::is_invocable_r<Convertible, Callable, Args...>::value;

template <class Callable, class... Args>
inline constexpr bool is_nothrow_invocable_v =
    std::is_nothrow_invocable<Callable, Args...>::value;

template <class Convertible, class Callable, class... Args>
inline constexpr bool is_nothrow_invocable_r_v =
    std::is_nothrow_invocable_r<Convertible, Callable, Args...>::value;
```

### <a name="parameters"></a>Paramètres

*Pouvant être appelé*\
Type pouvant être appelé à interroger.

*Attend*\
Types d’arguments à interroger.

*Implicit*\
Le type du résultat de *Callable* doit pouvoir être converti en.

## <a name="remarks"></a>Notes

Le `is_invocable` prédicat de type a la valeur true si le type  pouvant être appelé peut être appelé à l’aide des arguments *args* dans un contexte non évalué.

Le `is_invocable_r` prédicat de type a la valeur true si le type  pouvant être appelé peut être appelé à l’aide des arguments *args* dans un contexte non évalué pour produire un type de résultat convertible en *convertible*.

Le `is_nothrow_invocable` prédicat de type a la valeur true si le type pouvant être appelé peut être appelé à l’aide des arguments *args* dans un contexte non évalué, et que *ce type d'* appel est connu comme ne levant pas d’exception.

Le `is_nothrow_invocable_r` prédicat de type a la valeur true si le type  pouvant être appelé peut être appelé à l’aide des arguments *args* dans un contexte non évalué pour produire un type de résultat convertible en *convertible*, et qu’un tel appel est connu pour ne pas lever d’exception.

Chacun des types *convertibles*, *pouvant être appelés* et les types dans les *arguments* de package de paramètres doivent être un type complet, un tableau de limites inconnues ou un qui peut être qualifié de CV **`void`** . Sinon, le comportement du prédicat n’est pas défini.

## <a name="example"></a>Exemple

```cpp
// std__type_traits__is_invocable.cpp
// compile using: cl /EHsc /std:c++17 std__type_traits__is_invocable.cpp
#include <type_traits>

auto test1(int) noexcept -> int (*)()
{
    return nullptr;
}

auto test2(int) -> int (*)()
{
    return nullptr;
}

int main()
{
    static_assert( std::is_invocable<decltype(test1), short>::value );

    static_assert( std::is_invocable_r<int(*)(), decltype(test1), int>::value );
    static_assert( std::is_invocable_r<long(*)(), decltype(test1), int>::value ); // fails

    static_assert( std::is_nothrow_invocable<decltype(test1), int>::value );
    static_assert( std::is_nothrow_invocable<decltype(test2), int>::value ); // fails

    static_assert( std::is_nothrow_invocable_r<int(*)(), decltype(test1), int>::value );
    static_assert( std::is_nothrow_invocable_r<int(*)(), decltype(test2), int>::value ); // fails
}
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)
