---
title: mask_array (classe)
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 9da5e3593288be02819330e11b60e306784054dc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460141"
---
# <a name="maskarray-class"></a>mask_array (classe)

Classe de modèle interne auxiliaire qui prend en charge les objets qui sont des sous-ensembles de valarrays parents, spécifiés avec une expression booléenne, en fournissant des opérations entre les tableaux de sous-ensembles.

## <a name="syntax"></a>Syntaxe

## <a name="remarks"></a>Notes

La classe décrit un objet qui stocke une référence à un `va` objet de classe [valarray](../standard-library/valarray-class.md) **\<de type >** , ainsi qu' `ba` un objet de classe [\<valarray bool >](../standard-library/valarray-bool-class.md), qui décrit le séquence d’éléments à sélectionner à partir `valarray<Type>` de l’objet.

Vous construisez `mask_array<Type>` un objet uniquement en écrivant une expression de la forme [va&#91;BA&#93;](../standard-library/valarray-class.md#op_at). Les fonctions membres de la classe mask_array se comportent ensuite comme les signatures `valarray<Type>`de fonctions correspondantes définies pour, sauf que seule la séquence d’éléments sélectionnés est affectée.

La séquence se compose de au `ba.size` plus d’éléments. Un élément *J* n’est inclus que si **ba**[ *J*] a la valeur true. Par conséquent, il y a autant d’éléments dans la séquence qu’il y a `ba`d’éléments vrais dans. Si `I` est l’index de l’élément true le plus `ba`bas dans , va `I`[] est l’élément zéro dans la séquence sélectionnée.

## <a name="example"></a>Exemples

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

## <a name="requirements"></a>Configuration requise

**En-tête :** \<valarray>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
