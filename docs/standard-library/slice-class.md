---
title: slice, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::slice
- valarray/std::slice::size
- valarray/std::slice::start
- valarray/std::slice::stride
dev_langs:
- C++
helpviewer_keywords:
- std::slice [C++]
- std::slice [C++], size
- std::slice [C++], start
- std::slice [C++], stride
ms.assetid: 00f0b03d-d657-4b81-ba53-5a9034bb2bf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a2cff4aea707c98a4bce7060b16ce695d25c47d
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109004"
---
# <a name="slice-class"></a>slice, classe

Classe utilitaire de valarray qui sert à définir des sous-ensembles unidimensionnels d'un valarray parent. Si un valarray est considéré comme une matrice à deux dimensions avec tous les éléments dans un tableau, le secteur extrait un vecteur dans une dimension hors du tableau à deux dimensions.

## <a name="remarks"></a>Notes

La classe stocke les paramètres qui caractérisent un objet de type [slice_array](../standard-library/slice-array-class.md). Le sous-ensemble d’un valarray est construit indirectement quand un objet de la classe slice apparaît en tant qu’argument pour un objet de la classe [valarray](../standard-library/valarray-class.md#op_at)**\<Type>**. Les valeurs stockées qui spécifient le sous-ensemble sélectionné à partir du valarray parent sont les suivantes :

- un index de départ dans le valarray ;

- une longueur totale ou le nombre d'éléments dans le secteur ;

- une longueur ou distance entre les index d'éléments ultérieurs dans le valarray.

Si l'ensemble défini par un secteur est le sous-ensemble d'un valarray constant, le secteur est un nouveau valarray. Si l'ensemble défini par un secteur est le sous-ensemble d'un valarray non constant, le secteur a une sémantique de référence par rapport au valarray d'origine. Le mécanisme d'évaluation pour les valarrays non constants permet de gagner du temps et de la mémoire.

Les opérations sur les valarrays sont garanties uniquement si les sous-ensembles source et de destination définis par les secteurs sont distincts et que tous les index sont valides.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[slice](#slice)|Définit un sous-ensemble d'un `valarray` qui se compose d'un nombre d'éléments à égale distance les uns des autres et qui commencent à un élément spécifié.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[size](#size)|Recherche le nombre d'éléments dans un secteur d'un `valarray`.|
|[start](#start)|Recherche l'index de départ d'un secteur d'un `valarray`.|
|[stride](#stride)|Recherche la distance entre des éléments dans un secteur d'un `valarray`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<valarray>

**Espace de noms :** std

## <a name="size"></a>  slice::size

Recherche le nombre d’éléments dans une section d’un valarray.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans une section d’un valarray.

### <a name="example"></a>Exemple

```cpp
// slice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA, sizeVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   sizeVAR = vaSlice.size ( );
   cout << "The size of slice vaSlice is: "
        << sizeVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The size of the valarray is: 20.

The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The size of slice vaSlice is: 6.
```

## <a name="slice"></a>  slice::slice

Définit un sous-ensemble d’un valarray composé d’un nombre d’éléments qui sont à égale distance les uns des autres et qui commencent à un élément spécifié.

```cpp
slice();

slice(
    size_t _StartIndex,
    size_t _Len,
    size_t stride);
```

### <a name="parameters"></a>Paramètres

*_StartIndex*<br/>
Index valarray du premier élément dans le sous-ensemble.

*_Len*<br/>
Nombre d’éléments dans le sous-ensemble.

*stride*<br/>
Distance entre les éléments dans le sous-ensemble.

### <a name="return-value"></a>Valeur de retour

Le constructeur par défaut stocke des zéros pour l’index de départ, la longueur totale et le stride. Le deuxième constructeur stocke *_StartIndex* pour l’index de départ, *_Len* pour la longueur totale, et *stride* pour le stride.

### <a name="remarks"></a>Notes

Le stride peut être négatif.

### <a name="example"></a>Exemple

```cpp
// slice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  2 * (i + 1 );

   cout << "The operand valarray va is:\n( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 1 , 7 , 3 );
   vaResult = va [ vaSlice ];

   cout << "\nThe slice of valarray va is vaResult:"
        << "\nva[slice( 1, 7, 3)] = ( ";
      for ( i = 0 ; i < 7 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
( 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 ).

The slice of valarray va is vaResult:
va[slice( 1, 7, 3)] = ( 4 10 16 22 28 34 40 ).
```

## <a name="start"></a>  slice::start

Recherche l’index de départ d’une section d’un valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Valeur de retour

Index de départ d’une section d’un valarray.

### <a name="example"></a>Exemple

```cpp
// slice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t startVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] = i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   startVAR = vaSlice.start ( );
   cout << "The start index of slice vaSlice is: "
        << startVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The start index of slice vaSlice is: 3.
```

## <a name="stride"></a>  slice::stride

Recherche la distance entre les éléments dans une section d’un valarray.

```cpp
size_t stride() const;
```

### <a name="return-value"></a>Valeur de retour

Distance entre les éléments dans une section d’un valarray.

### <a name="example"></a>Exemple

```cpp
// slice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t strideVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  3 * ( i + 1 );

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 4 , 5 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 4, 5, 3)] =\n ( ";
      for ( i = 0 ; i < 5 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   strideVAR = vaSlice.stride ( );
   cout << "The stride of slice vaSlice is: "
        << strideVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45 48 51 54 57 60 ).
The slice of valarray va is vaResult = va[slice( 4, 5, 3)] =
( 15 24 33 42 51 ).
The stride of slice vaSlice is: 3.
```

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
