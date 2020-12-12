---
description: 'En savoir plus sur : classe indirect_array'
title: indirect_array, classe
ms.date: 11/04/2016
f1_keywords:
- valarray/std::indirect_array
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
ms.openlocfilehash: 47c9a0e604fd9873d7705f70624e67d9b3a22a7a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324039"
---
# <a name="indirect_array-class"></a>indirect_array, classe

Modèle de classe auxiliaire interne qui prend en charge les objets qui sont des sous-ensembles de valarrays en fournissant des opérations entre les tableaux de sous-ensembles définis en spécifiant un sous-ensemble d’index d’un valarray parent.

## <a name="syntax"></a>Syntaxe

## <a name="remarks"></a>Notes

La classe décrit un objet qui stocke une référence à un objet `va` de classe [valarray](../standard-library/valarray-class.md) **\<Type>** , ainsi qu’un objet `xa` de classe `valarray<size_t>` , qui décrit la séquence d’éléments à sélectionner à partir de l' `valarray<Type>` objet.

Vous construisez un `indirect_array<Type>` objet uniquement en écrivant une expression sous la forme `va[xa]` . Les fonctions membres de la classe indirect_array se comportent ensuite comme les signatures de fonctions correspondantes définies pour `valarray<Type>` , sauf que seule la séquence d’éléments sélectionnés est affectée.

La séquence se compose de **XA.** [dimensionner](../standard-library/valarray-class.md#size) les éléments, où `I` l’élément devient l’index **XA**[ `I` ] dans `va` .

## <a name="example"></a>Exemple :

```cpp
// indirect_array.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      va [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 2 )
      va [ i ] =  -1;

   cout << "The initial operand valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   // Select 2nd, 4th & 6th elements
   // and assign a value of 10 to them
   valarray<size_t> indx ( 3 );
   indx [0] = 2;
   indx [1] = 4;
   indx [2] = 6;
   va[indx] = 10;

   cout << "The modified operand valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;
}
```

### <a name="output"></a>Output

```cpp
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 10 -1 10 -1 10 -1 8 -1).
```

## <a name="requirements"></a>Spécifications

**En-tête :**\<valarray>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
