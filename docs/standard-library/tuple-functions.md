---
description: 'En savoir plus sur &lt; : &gt; fonctions de Tuple'
title: '&lt;tuple&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- tuple/std::get
- tuple/std::make_tuple
- tuple/std::tie
ms.assetid: bc6be38f-5258-4c14-b81b-63caa335fd44
helpviewer_keywords:
- std::get [C++]
- std::make_tuple [C++]
- std::tie [C++]
- std::get [C++]
- std::make_tuple [C++]
- std::tie [C++]
ms.openlocfilehash: cf58cab5f222594a935156cf7e7f2e886639da2b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168954"
---
# <a name="lttuplegt-functions"></a>&lt;tuple&gt;, fonctions

## <a name="apply"></a><a name="apply"></a> appliqu

```cpp
template <class F, class Tuple> constexpr decltype(auto) apply(F&& f, Tuple&& t);
```

### <a name="remarks"></a>Notes

Appelle la fonction *F* avec un Tuple *t*.

## <a name="forward_as_tuple"></a><a name="forward"></a> forward_as_tuple

```cpp
template <class... TTypes>
    constexpr tuple<TTypes&&...> forward_as_tuple(TTypes&&...) noexcept;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne `tuple<TTypes&&...>(std::forward<TTypes>(t)...)`.

### <a name="remarks"></a>Notes

Construit un tuple de références aux arguments dans *t* approprié pour le transfert en tant qu’arguments à une fonction.

## <a name="get"></a><a name="get"></a> Télécharger

Obtient un élément d’un objet `tuple` , par index ou par type (dans C++14).

```cpp
// by index:
// get reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr tuple_element_t<Index, tuple<Types...>>& get(tuple<Types...>& Tuple) noexcept;

// get const reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr const tuple_element_t<Index, tuple<Types...>>& get(const tuple<Types...>& Tuple) noexcept;

// get rvalue reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr tuple_element_t<Index, tuple<Types...>>&& get(tuple<Types...>&& Tuple) noexcept;

// (C++14) by type:
// get reference to T element of tuple
template <class T, class... Types>
   constexpr T& get(tuple<Types...>& Tuple) noexcept;

// get const reference to T element of tuple
template <class T, class... Types>
   constexpr const T& get(const tuple<Types...>& Tuple) noexcept;

// get rvalue reference to T element of tuple
template <class T, class... Types>
   constexpr T&& get(tuple<Types...>&& Tuple) noexcept;
```

### <a name="parameters"></a>Paramètres

*Index*\
Index de l’élément à obtenir.

*Modes*\
Séquence de types déclarés dans le tuple dans l’ordre de déclaration.

*T*\
Type de l’élément à obtenir.

*Passent*\
`std::tuple`Qui contient un nombre quelconque d’éléments.

### <a name="remarks"></a>Notes

Les fonctions de modèle retournent une référence à la valeur à l' *index* d’index ou de type *T* dans l' `tuple` objet.

L'appel de `get<T>(Tuple)` génère une erreur de compilation si le Tuple ne contient pas un seul élément de type T.

### <a name="example"></a>Exemple

```cpp
#include <tuple>
#include <iostream>
#include <string>

using namespace std;

int main() {
    tuple<int, double, string> tup(0, 1.42, "Call me Tuple");

    // get elements by index
    cout << " " << get<0>(tup);
    cout << " " << get<1>(tup);
    cout << " " << get<2>(tup) << endl;

    // get elements by type
    cout << " " << get<int>(tup);
    cout << " " << get<double>(tup);
    cout << " " << get<string>(tup) << endl;
}
```

```Output
0 1.42 Call me Tuple
0 1.42 Call me Tuple
```

## <a name="make_from_tuple"></a><a name="make_from_tuple"></a> make_from_tuple

```cpp
template <class T, class Tuple> constexpr T make_from_tuple(Tuple&& t);
```

### <a name="remarks"></a>Notes

Comme pour `return make_from_tuple_impl<T>(forward<Tuple>(t), make_index_sequence<tuple_size_v<decay_t<Tuple>>>{})`.

## <a name="make_tuple"></a><a name="make_tuple"></a> make_tuple

Crée un `tuple` à partir des valeurs de l’élément.

```cpp
template <class T1, class T2, ..., class TN>
   tuple<V1, V2, ..., VN> make_tuple(const T1& t1, const T2& t2, ..., const TN& tN);
```

### <a name="parameters"></a>Paramètres

*TN*\
Type du N-ième paramètre de fonction.

*tN*\
Valeur du N-ième paramètre de fonction.

### <a name="remarks"></a>Notes

La fonction de modèle retourne `tuple<V1, V2, ..., VN>(t1, t2, ..., tN)` , où chaque type `Vi` est `X&` lorsque le type correspondant `Ti` est `cv` `reference_wrapper<X>` ; sinon, il a `Ti` la valeur.

Un avantage de `make_tuple` est que les types d'objets stockés sont déterminés automatiquement par le compilateur et ne sont pas tenus d'être spécifiés explicitement. N'utilisez pas d'arguments template explicites, tels que `make_tuple<int, int>(1, 2)`, lorsque vous utilisez `make_tuple`, car cela est inutilement détaillé et ajoute des problèmes complexes de référence rvalue susceptibles de provoquer un échec de compilation.

### <a name="example"></a>Exemple

```cpp
// std__tuple__make_tuple.cpp
// compile by using: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0) << std::endl;

    c0 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0) << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
```

## <a name="swap"></a><a name="swap"></a> échange

```cpp
template <class... Types>
    void swap(tuple<Types...>& x, tuple<Types...>& y) noexcept(see below );
```

## <a name="tie"></a><a name="tie"></a> traverse

Crée un `tuple` à partir des références d’élément.

```cpp
template <class T1, class T2, ..., class TN>
tuple<T1&, T2&, ..., TN&> tie(T1& t1, T2& t2, ..., TN& tN);
```

### <a name="parameters"></a>Paramètres

*TN*\
Type de base du N-ième élément de tuple.

### <a name="remarks"></a>Notes

La fonction de modèle retourne `tuple<T1&, T2&, ..., TN&>(t1, t2, ..., tN)`.

### <a name="example"></a>Exemple

```cpp
// std__tuple__tie.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    int v4 = 4;
    double v5 = 5;
    int v6 = 6;
    double v7 = 7;
    std::tie(v4, v5, v6, v7) = c0;

// display contents " 0 1 2 3"
    std::cout << " " << v4;
    std::cout << " " << v5;
    std::cout << " " << v6;
    std::cout << " " << v7;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="tuple_cat"></a><a name="tuple_cat"></a> tuple_cat

```cpp
template <class... Tuples> constexpr tuple<CTypes...> tuple_cat(Tuples&&...);
```

### <a name="return-value"></a>Valeur renvoyée

Objet Tuple construit en initialisant chaque élément de type.

## <a name="tuple_element_t"></a><a name="tuple_element_t"></a> tuple_element_t

```cpp
template <size_t I, class T>
    using tuple_element_t = typename tuple_element<I, T>::type;
```

## <a name="tuple_size_v"></a><a name="tuple_size_v"></a> tuple_size_v

```cpp
template <class T>
    inline constexpr size_t tuple_size_v = tuple_size<T>::value;
```
