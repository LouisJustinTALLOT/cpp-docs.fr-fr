---
description: 'En savoir plus sur : &lt; classe bool valarray &gt;'
title: valarray&lt;bool&gt;, classe
ms.date: 11/04/2016
f1_keywords:
- valarray<bool>
- valarray/std::valarray<bool>
helpviewer_keywords:
- valarray<bool> class
ms.assetid: fc0e7121-4758-4ea5-86c3-f04448f04acf
ms.openlocfilehash: c646c03b16c2724d61310f75eb48a625530a6712
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153406"
---
# <a name="valarrayltboolgt-class"></a>valarray&lt;bool&gt;, classe

Une version spécialisée du modèle de classe **valarray \<Type>** aux éléments de type **`bool`** .

## <a name="syntax"></a>Syntaxe

```cpp
class valarray<bool>
```

## <a name="example"></a>Exemple

```cpp
// valarray_bool.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaBool ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
   for ( i = 0 ; i < 10 ; i++ )
      cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
   for ( i = 0 ; i < 10 ; i++ )
      cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaBool = ( vaL < vaR );
   cout << "The result of the less-than comparison "
   << "test is the\nvalarray<bool>: ( ";
   for ( i = 0 ; i < 10 ; i++ )
      cout << vaBool [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The result of the less-than comparison test is the
valarray<bool>: ( 0 0 1 0 1 0 1 0 1 0 ).
*/
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<valarray>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[valarray, classe](../standard-library/valarray-class.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
