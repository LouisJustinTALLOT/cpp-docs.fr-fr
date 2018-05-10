---
title: mask_array, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::mask_array
dev_langs:
- C++
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b19ac68f1d1db9ac73e0519b566f68443775db11
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
---
# <a name="maskarray-class"></a>mask_array, classe

Classe de modèle interne auxiliaire qui prend en charge les objets qui sont des sous-ensembles de valarrays parents, spécifiés avec une expression booléenne, en fournissant des opérations entre les tableaux de sous-ensembles.

## <a name="syntax"></a>Syntaxe

## <a name="remarks"></a>Notes

Cette classe décrit un objet qui stocke une référence à un objet **va** de classe [valarray](../standard-library/valarray-class.md)**\<Type>**, ainsi qu’un objet **ba** de classe [valarray\<bool>](../standard-library/valarray-bool-class.md), qui décrit la séquence d’éléments à sélectionner à partir de l’objet **valarray\<Type>**.

Vous construisez un objet **mask_array\<Type>** uniquement en écrivant une expression sous la forme [va&#91;ba&#93;](../standard-library/valarray-class.md#op_at). Les fonctions membres de classe mask_array se comportent ensuite comme les signatures de fonctions correspondantes définies pour **valarray\<Type>**, sauf que seule la séquence d’éléments sélectionnée est affectée.

La séquence se compose tout au plus de **ba.size** éléments. Un élément *J* n’est inclus que si **ba**[ *J*] a la valeur true. Par conséquent, il y a autant d’éléments dans la séquence qu’il y a d’éléments true dans **ba**. Si `I` est l’index de l’élément true le plus bas dans **ba**, **va**[ `I`] est l’élément zéro dans la séquence sélectionnée.

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

## <a name="requirements"></a>Spécifications

**En-tête :** \<valarray>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
