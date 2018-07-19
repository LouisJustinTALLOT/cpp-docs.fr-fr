---
title: indirect_array, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::indirect_array
dev_langs:
- C++
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 676cc8ea493d113e9ef8a6f85108fdf3bad6ce5f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959505"
---
# <a name="indirectarray-class"></a>indirect_array, classe

Classe de modèle interne auxiliaire qui prend en charge les objets qui sont des sous-ensembles de valarrays en fournissant des opérations entre des tableaux de sous-ensembles définis en spécifiant un sous-ensemble d'index d'un valarray parent.

## <a name="syntax"></a>Syntaxe

## <a name="remarks"></a>Notes

La classe décrit un objet qui stocke une référence à un objet `va` de classe [valarray](../standard-library/valarray-class.md)**\<Type >**, ainsi qu’un objet `xa` de classe `valarray<size_t>`, qui décrit la séquence d’éléments à sélectionner à partir de la `valarray<Type>` objet.

Vous construisez un `indirect_array<Type>` objet uniquement en écrivant une expression sous la forme `va[xa]`. Les fonctions membres de classe indirect_array se comportent ensuite comme les signatures de fonction correspondantes définies pour `valarray<Type>`, sauf que seule la séquence d’éléments sélectionnée est affectée.

La séquence se compose de **xa.** [taille](../standard-library/valarray-class.md#size) éléments, où élément `I` devient l’index **xa**[ `I`] dans `va`.

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

## <a name="requirements"></a>Configuration requise

**En-tête :** \<valarray>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
