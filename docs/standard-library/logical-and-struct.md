---
description: 'En savoir plus sur : struct logical_and'
title: logical_and, struct
ms.date: 11/04/2016
f1_keywords:
- functional/std::logical_and
helpviewer_keywords:
- logical_and class
- logical_and struct
ms.assetid: 1a375cc2-0592-4d57-a553-78009c7ad610
ms.openlocfilehash: 2d0cc8b8c40407356d8d3ba41046c0033941c2ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277698"
---
# <a name="logical_and-struct"></a>logical_and, struct

Objet de fonction prédéfini qui effectue l’opération de conjonction logique ( `operator&&` ) sur ses arguments.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type = void>
struct logical_and : public binary_function<Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator&&
template <>
struct logical_and<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) && std::forward<U>(Right));
};
```

### <a name="parameters"></a>Paramètres

*Type*, *T*, *U*\
Tout type qui prend en charge un `operator&&` qui accepte des opérandes des types spécifiés ou inférés.

*Gauche*\
Opérande gauche de l’opération de conjonction logique. Le modèle non spécialisé prend un argument de référence lvalue *de type type.* Le modèle spécialisé effectue un transfert parfait des arguments de la lvalue et de la référence rvalue du type déduit *T*.

*Oui*\
Opérande droit de l’opération de conjonction logique. Le modèle non spécialisé prend un argument de référence lvalue *de type type.* Le modèle spécialisé effectue un transfert parfait des arguments de la lvalue et de la référence rvalue du type inféré *U*.

## <a name="return-value"></a>Valeur renvoyée

Résultat de `Left && Right`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator&&`.

## <a name="remarks"></a>Notes

Pour les types définis par l’utilisateur, il n’y a aucun court-circuit d’évaluation de l’opérande. Les deux arguments sont évalués par `operator&&`.

## <a name="example"></a>Exemple

```cpp
// functional_logical_and.cpp
// compile with: /EHsc

#define _CRT_RAND_S
#include <stdlib.h>
#include <deque>
#include <algorithm>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   deque<bool> d1, d2, d3( 7 );
   deque<bool>::iterator iter1, iter2, iter3;

   unsigned int randomValue;

   int i;
   for ( i = 0 ; i < 7 ; i++ )
   {
      if ( rand_s( &randomValue ) == 0 )
      {
         d1.push_back((bool)(( randomValue % 2 ) != 0));
      }

   }

   int j;
   for ( j = 0 ; j < 7 ; j++ )
   {
      if ( rand_s( &randomValue ) == 0 )
      {
         d2.push_back((bool)(( randomValue % 2 ) != 0));
      }
   }

   cout << boolalpha;    // boolalpha I/O flag on

   cout << "Original deque:\n d1 = ( " ;
   for ( iter1 = d1.begin( ) ; iter1 != d1.end( ) ; iter1++ )
      cout << *iter1 << " ";
   cout << ")" << endl;

   cout << "Original deque:\n d2 = ( " ;
   for ( iter2 = d2.begin( ) ; iter2 != d2.end( ) ; iter2++ )
      cout << *iter2 << " ";
   cout << ")" << endl;

   // To find element-wise conjunction of the truth values
   // of d1 & d2, use the logical_and function object
   transform( d1.begin( ), d1.end( ), d2.begin( ),
      d3.begin( ), logical_and<bool>( ) );
   cout << "The deque which is the conjunction of d1 & d2 is:\n d3 = ( " ;
   for ( iter3 = d3.begin( ) ; iter3 != d3.end( ) ; iter3++ )
      cout << *iter3 << " ";
   cout << ")" << endl;
}
```

```Output
Original deque:
d1 = ( true true true true true false false )
Original deque:
d2 = ( true false true true false true false )
The deque which is the conjunction of d1 & d2 is:
d3 = ( true false true true false false false )
```
