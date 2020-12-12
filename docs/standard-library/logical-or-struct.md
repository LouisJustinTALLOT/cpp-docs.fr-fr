---
description: 'En savoir plus sur : struct logical_or'
title: logical_or (struct)
ms.date: 11/04/2016
f1_keywords:
- functional/std::logical_or
helpviewer_keywords:
- logical_or class
- logical_or struct
ms.assetid: ec8143f8-5755-4e7b-8025-507fb6bf6911
ms.openlocfilehash: 7b6578bb3405b2428724554d520ffe784b885a40
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277672"
---
# <a name="logical_or-struct"></a>logical_or (struct)

Objet de fonction prédéfini qui effectue l’opération de disjonction logique ( `operator||`) sur ses arguments.

## <a name="syntax"></a>Syntaxe

```
template <class Type = void>
struct logical_or : public binary_function<Type, Type, bool>
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator||
template <>
struct logical_or<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) || std::forward<U>(Right));
};
```

### <a name="parameters"></a>Paramètres

*Type*, *T*, *U*\
Tout type qui prend en charge un `operator||` qui accepte des opérandes des types spécifiés ou inférés.

*Gauche*\
Opérande gauche de l’opération de disjonction logique. Le modèle non spécialisé prend un argument de référence lvalue *de type type.* Le modèle spécialisé effectue un transfert parfait des arguments de la lvalue et de la référence rvalue du type déduit *T*.

*Oui*\
Opérande droit de l’opération de disjonction logique. Le modèle non spécialisé prend un argument de référence lvalue *de type type.* Le modèle spécialisé effectue un transfert parfait des arguments de la lvalue et de la référence rvalue du type inféré *U*.

## <a name="return-value"></a>Valeur renvoyée

Résultat de `Left || Right`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator||`.

## <a name="remarks"></a>Notes

Pour les types définis par l’utilisateur, il n’y a aucun court-circuit d’évaluation de l’opérande. Les deux arguments sont évalués par `operator||`.

## <a name="example"></a>Exemple

```cpp
// functional_logical_or.cpp
// compile with: /EHsc
#include <deque>
#include <algorithm>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   deque <bool> d1, d2, d3( 7 );
   deque <bool>::iterator iter1, iter2, iter3;

   int i;
   for ( i = 0 ; i < 7 ; i++ )
   {
      d1.push_back((bool)((rand() % 2) != 0));
   }

   int j;
   for ( j = 0 ; j < 7 ; j++ )
   {
      d2.push_back((bool)((rand() % 2) != 0));
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

   // To find element-wise disjunction of the truth values
   // of d1 & d2, use the logical_or function object
   transform( d1.begin( ), d1.end( ), d2.begin( ),
      d3.begin( ), logical_or<bool>( ) );
   cout << "The deque which is the disjuction of d1 & d2 is:\n d3 = ( " ;
   for ( iter3 = d3.begin( ) ; iter3 != d3.end( ) ; iter3++ )
      cout << *iter3 << " ";
   cout << ")" << endl;
}
```

```Output
Original deque:
d1 = ( true true false false true false false )
Original deque:
d2 = ( false false false true true true true )
The deque which is the disjuction of d1 & d2 is:
d3 = ( true true false true true true true )
```
