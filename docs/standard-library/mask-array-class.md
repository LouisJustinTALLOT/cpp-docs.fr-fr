---
title: mask_array (classe)
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 12398203d61f2c3ea155b5f6e6e7b118d4a13c75
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689403"
---
# <a name="mask_array-class"></a>mask_array (classe)

Modèle de classe auxiliaire interne qui prend en charge les objets qui sont des sous-ensembles de valarrays parents, spécifiés avec une expression booléenne, en fournissant des opérations entre les tableaux de sous-ensembles.

## <a name="syntax"></a>Syntaxe

## <a name="remarks"></a>Notes

La classe décrit un objet qui stocke une référence à un objet `va` de la classe [valarray](../standard-library/valarray-class.md)  **\<Type >** , ainsi qu’un `ba` d’objet de la classe [valarray \<bool](../standard-library/valarray-bool-class.md)>, qui décrit la séquence d’éléments à sélectionner. à partir de l’objet `valarray<Type>`.

Vous construisez un objet `mask_array<Type>` uniquement en écrivant une expression de [la&#91;forme&#93;va BA](../standard-library/valarray-class.md#op_at). Les fonctions membres de la classe mask_array se comportent ensuite comme les signatures de fonctions correspondantes définies pour `valarray<Type>`, sauf que seule la séquence d’éléments sélectionnés est affectée.

La séquence se compose d’au plus `ba.size` éléments. Un élément *J* n’est inclus que si **ba**[ *J*] a la valeur true. Par conséquent, il y a autant d’éléments dans la séquence qu’il y a de vrais éléments dans `ba`. Si `I` est l’index de l’élément true le plus bas dans `ba`, **va**[`I`] est l’élément zéro dans la séquence sélectionnée.

## <a name="example"></a>Exemple

```cpp
// mask_array.cpp
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

   // Use masked subsets to assign a value of 10
   // to all elements grrater than 3 in value
   va [va > 3 ] = 10;
   cout << "The modified operand valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;
}
```

### <a name="output"></a>Sortie

```Output
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 2 -1 10 -1 10 -1 10 -1).
```

## <a name="requirements"></a>spécifications

**En-tête :** \<valarray>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
