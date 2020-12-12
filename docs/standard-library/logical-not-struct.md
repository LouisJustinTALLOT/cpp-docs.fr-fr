---
description: 'En savoir plus sur : struct logical_not'
title: logical_not (struct)
ms.date: 11/04/2016
f1_keywords:
- functional/std::logical_not
helpviewer_keywords:
- logical_not class
- logical_not struct
ms.assetid: 892db678-31da-4540-974b-17b05efc0849
ms.openlocfilehash: dc89a5a764d9f3182609b47c5f05eb8b3e167cec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277685"
---
# <a name="logical_not-struct"></a>logical_not (struct)

Objet de fonction prédéfini qui effectue l’opération NOT logique ( `operator!` ) sur son argument.

## <a name="syntax"></a>Syntaxe

```
template <class Type = void>
struct logical_not : public unary_function<Type, bool>
{
    bool operator()(const Type& Left) const;
};

// specialized transparent functor for operator!
template <>
struct logical_not<void>
{
  template <class Type>
  auto operator()(Type&& Left) const`
     -> decltype(!std::forward<Type>(Left));
};
```

### <a name="parameters"></a>Paramètres

*Entrer*\
Tout type qui prend en charge un `operator!` qui accepte un opérande du type spécifié ou déduit.

*Gauche*\
Opérande de l’opération NOT logique. Le modèle non spécialisé prend un argument de référence lvalue *de type type.* Le modèle spécialisé effectue un transfert parfait des arguments de la lvalue et de la référence rvalue du *type* inféré.

## <a name="return-value"></a>Valeur renvoyée

Résultat de `!Left`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator!`.

## <a name="example"></a>Exemple

```cpp
// functional_logical_not.cpp
// compile with: /EHsc
#include <deque>
#include <algorithm>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   deque<bool> d1, d2 ( 7 );
   deque<bool>::iterator iter1, iter2;

   int i;
   for ( i = 0 ; i < 7 ; i++ )
   {
      d1.push_back((bool)((i % 2) != 0));
   }

   cout << boolalpha;    // boolalpha I/O flag on

   cout << "Original deque:\n d1 = ( " ;
   for ( iter1 = d1.begin( ) ; iter1 != d1.end( ) ; iter1++ )
      cout << *iter1 << " ";
   cout << ")" << endl;

   // To flip all the truth values of the elements,
   // use the logical_not function object
   transform( d1.begin( ), d1.end( ), d2.begin( ),logical_not<bool>( ) );
   cout << "The deque with its values negated is:\n d2 = ( " ;
   for ( iter2 = d2.begin( ) ; iter2 != d2.end( ) ; iter2++ )
      cout << *iter2 << " ";
   cout << ")" << endl;
}
```

```Output
Original deque:
d1 = ( false true false true false true false )
The deque with its values negated is:
d2 = ( true false true false true false true )
```
