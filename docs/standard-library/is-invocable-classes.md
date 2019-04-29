---
title: is_invocable, is_invocable_r, is_nothrow_invocable, classes d’is_nothrow_invocable_r
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
ms.openlocfilehash: bb5e75a897029ded2e00e491d93d2df41a3e115b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336229"
---
# <a name="isinvocable-isinvocabler-isnothrowinvocable-isnothrowinvocabler-classes"></a>is_invocable, is_invocable_r, is_nothrow_invocable, classes d’is_nothrow_invocable_r

Ces modèles déterminent si un type peut être appelé avec les types d’arguments spécifiés. `is_invocable_r` et `is_nothrow_invocable_r` également déterminer si le résultat de l’appel est convertible en un type spécifique. `is_nothrow_invocable` et `is_nothrow_invocable_r` également déterminer si l’appel ne connaît ne pas lever d’exceptions. Ajouté dans C ++ 17.

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

*Callable*<br/>
Type pouvant être appelé à interroger.

*Args*<br/>
Les types d’arguments à interroger.

*Convertible*<br/>
Le type du résultat de *joignable* doit être convertible en.

## <a name="remarks"></a>Notes

Le `is_invocable` prédicat de type a la valeur true si le type pouvant être appelé *joignable* peuvent être appelées à l’aide des arguments *Args* dans un contexte non évalué.

Le `is_invocable_r` prédicat de type a la valeur true si le type pouvant être appelé *joignable* peuvent être appelées à l’aide des arguments *Args* dans un contexte non évalué pour produire un résultat type convertibles en  *Convertible*.

Le `is_nothrow_invocable` prédicat de type a la valeur true si le type pouvant être appelé *joignable* peuvent être appelées à l’aide des arguments *Args* dans un contexte non évalué et qu’un tel appel ne connaît ne pas lever une exception.

Le `is_nothrow_invocable_r` prédicat de type a la valeur true si le type pouvant être appelé *joignable* peuvent être appelées à l’aide des arguments *Args* dans un contexte non évalué pour produire un résultat type convertibles en  *Convertible*, et que cet appel ne connaît ne pas lever une exception.

Chacun des types *Convertible*, *joignable*et les types dans le package de paramètres *Args* doit être un type complet, un tableau de limite inconnue ou un éventuellementqualifiédecv**void**. Sinon, le comportement du prédicat est indéfini.

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

## <a name="requirements"></a>Configuration requise

**En-tête :** \<type_traits>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<type_traits>](../standard-library/type-traits.md)<br/>
[invoke](functional-functions.md#invoke)<br/>
