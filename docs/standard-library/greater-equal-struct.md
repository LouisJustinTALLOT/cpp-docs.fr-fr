---
description: 'En savoir plus sur : struct greater_equal'
title: greater_equal (struct)
ms.date: 11/04/2016
f1_keywords:
- functional/std::greater_equal
helpviewer_keywords:
- greater_equal struct
- greater_equal function
ms.assetid: a8ba911b-7af8-4653-b972-d8618f4df7d5
ms.openlocfilehash: 33d1758c0031d2767f9a9ba0238f0f0af1fa7595
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232055"
---
# <a name="greater_equal-struct"></a>greater_equal (struct)

Prédicat binaire qui effectue l’opération « supérieur à » ou « égal à » ( `operator>=` ) sur ses arguments.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type = void>
struct greater_equal : public binary_function <Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator>=
template <>
struct greater_equal<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left)>= std::forward<U>(Right));
};
```

### <a name="parameters"></a>Paramètres

*Type*, *T*, *U*\
Tout type qui prend en charge un `operator>=` qui accepte des opérandes des types spécifiés ou inférés.

*Gauche*\
Opérande gauche de l’opération Supérieur ou égal à. Le modèle non spécialisé prend un argument de référence lvalue *de type type.* Le modèle spécialisé effectue un transfert parfait des arguments de la lvalue et de la référence rvalue du type déduit *T*.

*Oui*\
Opérande droit de l’opération Supérieur ou égal à. Le modèle non spécialisé prend un argument de référence lvalue *de type type.* Le modèle spécialisé effectue un transfert parfait des arguments de la lvalue et de la référence rvalue du type inféré *U*.

## <a name="return-value"></a>Valeur renvoyée

Résultat de `Left >= Right`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator>=`.

## <a name="remarks"></a>Notes

Le prédicat binaire `greater_equal` < `Type`> fournit un classement faible strict d’un ensemble de valeurs d’élément de type *type* dans des classes d’équivalence, si et seulement si ce type satisfait les exigences mathématiques standard pour être classé. Les spécialisations de tout type pointeur produisent un ordre total des éléments, dans le sens où tous les éléments de valeurs distinctes sont ordonnés les uns par rapport aux autres.

## <a name="example"></a>Exemple

```cpp
// functional_greater_equal.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <cstdlib>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   v1.push_back( 6262 );
   v1.push_back( 6262 );
   for ( i = 0 ; i < 5 ; i++ )
   {
      v1.push_back( rand( ) );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use default binary predicate less<int>( )
   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order,
   // specify binary predicate greater_equal<int>( )
   sort( v1.begin( ), v1.end( ), greater_equal<int>( ) );
   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (6262 6262 41 18467 6334 26500 19169)
Sorted vector v1 = (41 6262 6262 6334 18467 19169 26500)
Resorted vector v1 = (26500 19169 18467 6334 6262 6262 41)
```
