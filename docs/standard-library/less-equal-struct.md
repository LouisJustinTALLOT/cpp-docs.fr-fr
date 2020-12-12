---
description: 'En savoir plus sur : struct less_equal'
title: less_equal (struct)
ms.date: 11/04/2016
f1_keywords:
- functional/std::less_equal
helpviewer_keywords:
- less_equal function
- less_equal struct
ms.assetid: 32085782-c7e0-4310-9b40-8aa3c1bff211
ms.openlocfilehash: b2d715971c5278629a6ea812c5a9c199f00c4a07
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312889"
---
# <a name="less_equal-struct"></a>less_equal (struct)

Prédicat binaire qui effectue l’opération « inférieur à » ou « égal à » ( `operator<=` ) sur ses arguments.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type = void>
struct less_equal : public binary_function <Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator<=
template <>
struct less_equal<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const
    -> decltype(std::forward<T>(Left) <= std::forward<U>(Right));
};
```

### <a name="parameters"></a>Paramètres

*Type*, *T*, *U*\
Tout type qui prend en charge un `operator<=` qui accepte des opérandes des types spécifiés ou inférés.

*Gauche*\
Opérande gauche de l’opération Inférieur ou égal à. Le modèle non spécialisé prend un argument de référence lvalue *de type type.* Le modèle spécialisé effectue un transfert parfait des arguments de la lvalue et de la référence rvalue du type déduit *T*.

*Oui*\
Opérande droit de l’opération Inférieur ou égal à. Le modèle non spécialisé prend un argument de référence lvalue *de type type.* Le modèle spécialisé effectue un transfert parfait des arguments de la lvalue et de la référence rvalue du type inféré *U*.

## <a name="return-value"></a>Valeur renvoyée

Résultat de `Left <= Right`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator<=`.

## <a name="remarks"></a>Notes

Le prédicat binaire `less_equal` < `Type`> fournit un classement faible strict d’un ensemble de valeurs d’élément de type *type* dans des classes d’équivalence, si et seulement si ce type satisfait les exigences mathématiques standard pour être classé. Les spécialisations de tout type pointeur produisent un ordre total des éléments, dans le sens où tous les éléments de valeurs distinctes sont ordonnés les uns par rapport aux autres.

## <a name="example"></a>Exemple

```cpp
// functional_less_equal.cpp
// compile with: /EHsc
#define _CRT_RAND_S
#include <stdlib.h>
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
   vector <int>::reverse_iterator rIter1;
   unsigned int randomNumber;

   int i;
   for ( i = 0 ; i < 5 ; i++ )
   {
      if ( rand_s( &randomNumber ) == 0 )
      {
         // Convert the random number to be between 1 - 50000
         // This is done for readability purposes
         randomNumber = ( unsigned int) ((double)randomNumber /
            (double) UINT_MAX * 50000) + 1;

         v1.push_back( randomNumber );
      }
   }
   for ( i = 0 ; i < 3 ; i++ )
   {
      v1.push_back( 2836 );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use the binary predicate less_equal<int>( )
   sort( v1.begin( ), v1.end( ), less_equal<int>( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (31247 37154 48755 15251 6205 2836 2836 2836)
Sorted vector v1 = (2836 2836 2836 6205 15251 31247 37154 48755)
```
