---
title: greater (struct)
ms.date: 11/04/2016
f1_keywords:
- functional/std::greater
helpviewer_keywords:
- greater struct
- greater function
ms.assetid: ebc348e1-edcd-466b-b21a-db95bd8f9079
ms.openlocfilehash: 7867de3a56893499f8d705e81ac3b34fabcf188c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159481"
---
# <a name="greater-struct"></a>greater (struct)

Un prédicat binaire qui effectue la plus grande-que l’opération (`operator>`) sur ses arguments.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type = void>
struct greater : public binary_function <Type, Type, bool>
{
    bool operator()(
    const Type& Left,
    const Type& Right) const;

};

// specialized transparent functor for operator>
template <>
struct greater<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const
    ->  decltype(std::forward<T>(Left)> std::forward<U>(Right));
};
```

### <a name="parameters"></a>Paramètres

*Type*, *T*, *U* n’importe quel type qui prend en charge un `operator>` qui accepte des opérandes des types spécifiés ou inférés.

*Gauche*<br/>
Opérande gauche de l’opération Supérieur à. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *T*.

*Droite*<br/>
Opérande droit de l’opération Supérieur à. Le modèle non spécialisé prend un argument de référence lvalue de type *Type*. Le modèle spécialisé effectue un transfert de lvalue parfait et type de déduire les arguments de référence rvalue de *U*.

## <a name="return-value"></a>Valeur de retour

Résultat de `Left > Right`. Le modèle spécialisé effectue un transfert parfait du résultat, qui a le type retourné par `operator>`.

## <a name="remarks"></a>Notes

Le prédicat binaire `greater` <  `Type`> fournit un ordre faible strict d’un ensemble de valeurs d’éléments de type *Type* dans des classes d’équivalence, si et seulement si ce type remplit la norme mathématique configuration requise pour donc classées. Les spécialisations de tout type pointeur produisent un ordre total des éléments, dans le sens où tous les éléments de valeurs distinctes sont ordonnés les uns par rapport aux autres.

## <a name="example"></a>Exemple

```cpp
// functional_greater.cpp
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
   for ( i = 0 ; i < 8 ; i++ )
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
   // specify binary predicate greater<int>( )
   sort( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (41 18467 6334 26500 19169 15724 11478 29358)
Sorted vector v1 = (41 6334 11478 15724 18467 19169 26500 29358)
Resorted vector v1 = (29358 26500 19169 18467 15724 11478 6334 41)
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<functional>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
