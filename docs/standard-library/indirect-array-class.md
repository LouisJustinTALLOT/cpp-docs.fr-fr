---
title: indirect_array, classe
ms.date: 11/04/2016
f1_keywords:
- valarray/std::indirect_array
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
ms.openlocfilehash: 5db5f2ce60038267b70ae8e77d9dd929d972af6a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456327"
---
# <a name="indirectarray-class"></a>indirect_array, classe

Classe de modèle interne auxiliaire qui prend en charge les objets qui sont des sous-ensembles de valarrays en fournissant des opérations entre des tableaux de sous-ensembles définis en spécifiant un sous-ensemble d'index d'un valarray parent.

## <a name="syntax"></a>Syntaxe

## <a name="remarks"></a>Notes

La classe décrit un objet qui stocke une référence à un `va` objet de classe [valarray](../standard-library/valarray-class.md) **\<de type >** , ainsi qu' `xa` un objet `valarray<size_t>`de classe, qui décrit la séquence d’éléments à sélectionner. `valarray<Type>` objet.

Vous construisez `indirect_array<Type>` un objet uniquement en écrivant une expression sous `va[xa]`la forme. Les fonctions membres de la classe indirect_array se comportent ensuite comme les signatures `valarray<Type>`de fonctions correspondantes définies pour, sauf que seule la séquence d’éléments sélectionnés est affectée.

La séquence se compose de **XA.** [dimensionner](../standard-library/valarray-class.md#size) les éléments, `I` où l’élément devient l' `I`index XA [] dans.  `va`

## <a name="example"></a>Exemple :

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

### <a name="output"></a>Sortie

```cpp
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 10 -1 10 -1 10 -1 8 -1).
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<valarray>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
