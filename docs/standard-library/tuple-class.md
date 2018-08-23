---
title: tuple, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- tuple/std::tuple
- tuple/std::tuple::operator=
dev_langs:
- C++
helpviewer_keywords:
- tuple class
ms.assetid: c38749be-ae4d-41f3-98ea-6aa3250de9a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc5f5c987f8e448490a0d337517d7a0699619849
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42539804"
---
# <a name="tuple-class"></a>tuple, classe

Encapsule une séquence d’éléments de longueur fixe.

## <a name="syntax"></a>Syntaxe

```
class tuple {
public:
   tuple();
   explicit tuple(P1, P2, ..., PN); // 0 < N
   tuple(const tuple&);
   template <class U1, class U2, ..., class UN>
      tuple(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>
      tuple(const pair<U1, U2>&); // N == 2

   void swap(tuple& right);
   tuple& operator=(const tuple&);
   template <class U1, class U2, ..., class UN>
      tuple& operator=(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>
      tuple& operator=(const pair<U1, U2>&); // N == 2
   };
```

### <a name="parameters"></a>Paramètres

*TN*  
 Type du Nième élément de tuple.

## <a name="remarks"></a>Notes

La classe de modèle décrit un objet qui stocke des objets de N de types `T1`, `T2`,..., `TN`, respectivement, où `0 <= N <= Nmax`. L’étendue d’une instance de tuple `tuple<T1, T2, ..., TN>` correspond au nombre `N` de ses arguments template. L’index de l’argument template `Ti` et de la valeur stockée correspondante de ce type est `i - 1`. Par conséquent, pendant que nous numéroter les types à partir de 1 à N dans cette documentation, l’index correspondant les valeurs comprises entre 0 et N - 1.

## <a name="example"></a>Exemple

```cpp
// tuple.cpp
// compile with: /EHsc

#include <vector>
#include <iomanip>
#include <iostream>
#include <tuple>
#include <string>

using namespace std;

typedef tuple <int, double, string> ids;

void print_ids(const ids& i)
{
   cout << "( "
        << get<0>(i) << ", "
        << get<1>(i) << ", "
        << get<2>(i) << " )." << endl;
}

int main( )
{
   // Using the constructor to declare and initialize a tuple
   ids p1(10, 1.1e-2, "one");

   // Compare using the helper function to declare and initialize a tuple
   ids p2;
   p2 = make_tuple(10, 2.22e-1, "two");

   // Making a copy of a tuple
   ids p3(p1);

   cout.precision(3);
   cout << "The tuple p1 is: ( ";
   print_ids(p1);
   cout << "The tuple p2 is: ( ";
   print_ids(p2);
   cout << "The tuple p3 is: ( ";
   print_ids(p3);

   vector<ids> v;

   v.push_back(p1);
   v.push_back(p2);
   v.push_back(make_tuple(3, 3.3e-2, "three"));

   cout << "The tuples in the vector are" << endl;
   for(vector<ids>::const_iterator i = v.begin(); i != v.end(); ++i)
   {
      print_ids(*i);
   }
}
```

```Output
The tuple p1 is: ( 10, 0.011, one ).
The tuple p2 is: ( 10, 0.222, two ).
The tuple p3 is: ( 10, 0.011, one ).
The tuples in the vector are
( 10, 0.011, one ).
( 10, 0.222, two ).
( 3, 0.033, three ).
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<tuple>

**Espace de noms :** std

## <a name="op_eq"></a>  tuple::operator=

Assigne un objet `tuple`.

```cpp
tuple& operator=(const tuple& right);

template <class U1, class U2, ..., class UN>
   tuple& operator=(const tuple<U1, U2, ..., UN>& right);

template <class U1, class U2>
   tuple& operator=(const pair<U1, U2>& right); // N == 2

tuple& operator=(tuple&& right);

template <class U1, class U2>
   tuple& operator=(pair<U1, U2>&& right);
```

### <a name="parameters"></a>Paramètres

*ANNULER*  
 Type du Nième élément de tuple copié.

*right*  
 Tuple à partir duquel effectuer la copie.

### <a name="remarks"></a>Notes

Les deux premiers opérateurs membres assignent les éléments de *droit* aux éléments correspondants de `*this`. Le troisième opérateur membre assigne `right.first` à l’élément à l’index 0 de `*this` et `right.second` à l’élément à l’index 1. Ces trois opérateurs membres retournent `*this`.

Les opérateurs membres restants sont analogues aux précédents, mais avec le [déclarateur de référence rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md).

### <a name="example"></a>Exemple

```cpp
// std__tuple__tuple_operator_as.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>
#include <utility>

typedef std::tuple<int, double, int, double> Mytuple;
int main()
    {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1;
    c1 = c0;

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c1);
    std::cout << " " << std::get<1>(c1);
    std::cout << " " << std::get<2>(c1);
    std::cout << " " << std::get<3>(c1);
    std::cout << std::endl;

    std::tuple<char, int> c2;
    c2 = std::make_pair('x', 4);

// display contents " x 4"
    std::cout << " " << std::get<0>(c2);
    std::cout << " " << std::get<1>(c2);
    std::cout << std::endl;

    return (0);
    }

```

```Output
0 1 2 3
0 1 2 3
x 4
```

## <a name="tuple_swap"></a>  tuple:swap

Échange les éléments de deux tuples.

```cpp
template <class... Types>
   void swap(tuple<Types...&> left, tuple<Types...&> right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*left*|Un tuple dont les éléments doivent être échangés avec ceux du tuple *droit*.|
|*right*|Un tuple dont les éléments doivent être échangés avec ceux du tuple *gauche*.|

### <a name="remarks"></a>Notes

La fonction exécute `left.swap(right)`.

## <a name="tuple"></a>  tuple::tuple

Construit un objet `tuple`.

```cpp
constexpr tuple();
explicit constexpr tuple(const Types&...);
template <class... UTypes>
   explicit constexpr tuple(UTypes&&...);

tuple(const tuple&) = default;
tuple(tuple&&) = default;

template <class... UTypes>
   constexpr tuple(const tuple<UTypes...>&);
template <class... UTypes>
   constexpr tuple(tuple<UTypes...>&&);

// only if sizeof...(Types) == 2
template <class U1, class U2>
   constexpr tuple(const pair<U1, U2>&);
template <class U1, class U2>
   constexpr tuple(pair<U1, U2>&&);
```

### <a name="parameters"></a>Paramètres

*ANNULER*  
 Type du Nième élément de tuple copié.

*right*  
 Tuple à partir duquel effectuer la copie.

### <a name="remarks"></a>Notes

Le premier constructeur construit un objet dont les éléments sont construits par défaut.

Le second constructeur construit un objet dont les éléments sont construits par copie à partir des arguments `P1`, `P2`, ..., `PN` avec chaque `Pi` initialisant l'élément à l'index `i - 1`.

Les troisième et quatrième constructeurs construisent un objet dont les éléments sont construits à partir de l’élément correspondant par copie *droit*.

Le cinquième constructeur construit un objet dont l'élément à l'index 0 est construit par copie à partir de `right.first` et dont l'élément à l'index 1 est construit par copie à partir de `right.second`.

Les constructeurs restants sont analogues aux précédents, mais avec le [déclarateur de référence rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md).

### <a name="example"></a>Exemple

```cpp
// std__tuple__tuple_tuple.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>
#include <utility>

typedef std::tuple<int, double, int, double> Mytuple;
int main()
    {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1;
    c1 = c0;

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c1);
    std::cout << " " << std::get<1>(c1);
    std::cout << " " << std::get<2>(c1);
    std::cout << " " << std::get<3>(c1);
    std::cout << std::endl;

    std::tuple<char, int> c2(std::make_pair('x', 4));

// display contents " x 4"
    std::cout << " " << std::get<0>(c2);
    std::cout << " " << std::get<1>(c2);
    std::cout << std::endl;

    Mytuple c3(c0);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c3);
    std::cout << " " << std::get<1>(c3);
    std::cout << " " << std::get<2>(c3);
    std::cout << " " << std::get<3>(c3);
    std::cout << std::endl;

    typedef std::tuple<int, float, int, float> Mytuple2;
    Mytuple c4(Mytuple2(4, 5, 6, 7));

// display contents " 4 5 6 7"
    std::cout << " " << std::get<0>(c4);
    std::cout << " " << std::get<1>(c4);
    std::cout << " " << std::get<2>(c4);
    std::cout << " " << std::get<3>(c4);
    std::cout << std::endl;

    return (0);
    }
```

```Output
 0 1 2 3
 0 1 2 3
 x 4
 0 1 2 3
 4 5 6 7
```

## <a name="see-also"></a>Voir aussi

[\<tuple>](../standard-library/tuple.md)<br/>
[make_tuple](../standard-library/tuple-functions.md#make_tuple)<br/>
