---
title: integer_sequence, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::index_sequence
- type_traits/std::make_index_sequence
- type_traits/std::integer_sequence
- type_traits/std::make_integer_sequence
- type_traits/std::index_sequence_for
dev_langs:
- C++
helpviewer_keywords:
- std::index_sequence
- std::make_index_sequence
- std::integer_sequence
- std::make_integer_sequence
- std::index_sequence_for
ms.assetid: 2cfdddee-819d-478e-bb78-c8a9c2696803
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 58700d1f52189afb1d8baf3456bac4ed84920fab
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846176"
---
# <a name="integersequence-class"></a>integer_sequence, classe

Représente une séquence d'entiers. Peut servir à déduire et à développer des packs de paramètres dans les types variadiques tels que std::tuple\<T...> qui sont passés comme arguments à une fonction.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>Paramètres

T le type des valeurs ; doit être un type intégral : bool, char, char16_t, char32_t, wchar_t, signé ou entier non signé.

Pack de paramètre sans type ourbes A qui représente une séquence de valeurs de type intégral T.

## <a name="members"></a>Membres

|||
|-|-|
|`static size_t size() noexcept`|Nombre d'éléments dans la séquence.|
|typedef T value_type|Type de chaque élément dans la séquence. Doit être un type intégral.|

## <a name="remarks"></a>Notes

Un pack de paramètres transmis directement à une fonction peut être décompressé sans aucun programme d'assistance de bibliothèque spécial. Quand un pack de paramètres fait partie d'un type qui est passé à une fonction et que vous avez besoin d'index pour accéder aux éléments, le moyen le plus simple de le décompresser consiste à utiliser `integer_sequence` et ses alias de types connexes `make_integer_sequence`, `index_sequence`, `make_index_sequence` et `index_sequence_for`.

## <a name="example"></a>Exemple

L’exemple suivant est basé sur la proposition d’origine [N3658](http://open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html). Il montre comment utiliser un `integer_sequence` pour créer un `std::tuple` à partir d'un `std::array<T,N>` et comment utiliser un `integer_sequence` pour accéder aux membres de tuple.

Dans la fonction `a2t`, un `index_sequence` est un alias de `integer_sequence` basé sur le type intégral `size_t`. `make_index_sequence` est un alias qui, au moment de la compilation, crée un `index_sequence` de base zéro avec le même nombre d'éléments que le tableau qui est passé par l'appelant. `a2t` transmet le `index_sequence` par valeur à `a2t_`, où l'expression `a[I]...` décompresse `I`, puis les éléments sont transmis à `make_tuple`, qui les consomme en tant qu'arguments individuels. Par exemple, si la séquence contient trois éléments, `make_tuple` est appelé comme make_tuple(a[0], a[1], a[2]). Les éléments du tableau proprement dits peuvent bien entendu être de n'importe quel type.

La fonction apply accepte un [std::tuple](../standard-library/tuple-class.md) et produit un integer_sequence à l’aide de la classe d’assistance `tuple_size`. Notez que [std::decay_t](../standard-library/decay-class.md) est nécessaire car [tuple_size](../standard-library/tuple-size-class-tuple.md) ne fonctionne pas avec les types référence. La fonction `apply_` décompresse les membres de tuple et les transmet en tant qu'arguments séparés à un appel de fonction. Dans cet exemple, la fonction est une expression lambda simple qui imprime les valeurs.

```

#include <stddef.h>
#include <iostream>
#include <tuple>
#include <utility>
#include <array>
#include <string>

using namespace std;

// Create a tuple from the array and the index_sequence
template<typename Array, size_t... I>
auto a2t_(const Array& a, index_sequence<I...>)
{
    return make_tuple(a[I]...);
}

// Create an index sequence for the array, and pass it to the
// implementation function a2t_
template<typename T, size_t N>
auto a2t(const array<T, N>& a)
{
    return a2t_(a, make_index_sequence<N>());
}

// Call function F with the tuple members as separate arguments.
template<typename F, typename Tuple = tuple<T...>, size_t... I>
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)
{
    return forward<F>(f)(get<I>(forward<Tuple>(args))...);
}

// Create an index_sequence for the tuple, and pass it with the
// function object and the tuple to the implementation function apply_
template<typename F, typename Tuple = tuple<T...>>
decltype(auto) apply(F&& f, Tuple&& args)
{
    using Indices = make_index_sequence<tuple_size<decay_t<Tuple>>::value >;
    return apply_(forward<F>(f), forward<Tuple>(args), Indices());
}

int main()
{
    const array<string, 3> arr { "Hello", "from", "C++14" };

    //Create a tuple given a array
    auto tup = a2t(arr);

    // Extract the tuple elements
    apply([](const string& a, const string& b, const string& c) {cout << a << " " << b << " " << c << endl; }, tup);

    char c;
    cin >> c;
}

```

Pour créer un `index_sequence` pour un pack de paramètres, utilisez `index_sequence_for`\<T...>, qui est un alias pour `make_index_sequence`\<sizeof...(T)>

## <a name="requirements"></a>Spécifications

En-tête : <type_traits>

Espace de noms : std

## <a name="see-also"></a>Voir aussi

[Ellipses et modèles variadiques](../cpp/ellipses-and-variadic-templates.md)<br/>
