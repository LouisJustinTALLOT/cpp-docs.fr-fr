---
title: indirect_array, classe
ms.date: 11/04/2016
f1_keywords:
- valarray/std::indirect_array
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
ms.openlocfilehash: 6be0c5153cbc94d09b414fc9e14fa498c7a4cfa7
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687916"
---
# <a name="indirect_array-class"></a>indirect_array, classe

Modèle de classe auxiliaire interne qui prend en charge les objets qui sont des sous-ensembles de valarrays en fournissant des opérations entre les tableaux de sous-ensembles définis en spécifiant un sous-ensemble d’index d’un valarray parent.

## <a name="syntax"></a>Syntaxe

## <a name="remarks"></a>Notes

La classe décrit un objet qui stocke une référence à un objet `va` de la classe [valarray](../standard-library/valarray-class.md)  **\<Type >** , ainsi qu’un `xa` d’objet de la classe `valarray<size_t>`, qui décrit la séquence d’éléments à sélectionner à partir de l’objet `valarray<Type>`.

Vous construisez un objet `indirect_array<Type>` uniquement en écrivant une expression sous la forme `va[xa]`. Les fonctions membres de la classe indirect_array se comportent ensuite comme les signatures de fonctions correspondantes définies pour `valarray<Type>`, sauf que seule la séquence d’éléments sélectionnés est affectée.

La séquence se compose de **XA.** [dimensionner](../standard-library/valarray-class.md#size) les éléments, où l’élément `I` devient l’index **XA**[`I`] dans `va`.

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

### <a name="output"></a>Sortie

```cpp
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 10 -1 10 -1 10 -1 8 -1).
```

## <a name="requirements"></a>spécifications

**En-tête :** \<valarray>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
