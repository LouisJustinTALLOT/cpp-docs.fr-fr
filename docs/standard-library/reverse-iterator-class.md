---
description: 'En savoir plus sur : classe reverse_iterator'
title: reverse_iterator, classe
ms.date: 03/27/2019
f1_keywords:
- xutility/std::reverse_iterator
- iterator/std::reverse_iterator::difference_type
- iterator/std::reverse_iterator::iterator_type
- iterator/std::reverse_iterator::pointer
- iterator/std::reverse_iterator::reference
- iterator/std::reverse_iterator::base
- iterator/std::reverse_iterator::operator_star
helpviewer_keywords:
- std::reverse_iterator [C++]
- std::reverse_iterator [C++], difference_type
- std::reverse_iterator [C++], iterator_type
- std::reverse_iterator [C++], pointer
- std::reverse_iterator [C++], reference
- std::reverse_iterator [C++], base
- std::reverse_iterator [C++], operator_star
ms.assetid: c0b34d04-ae9a-4999-9aff-28b313897ffa
ms.openlocfilehash: 0aa8b03188d8b5a6e2ce004579b7b3cc2fb9b254
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148965"
---
# <a name="reverse_iterator-class"></a>reverse_iterator, classe

Le modèle de classe est un adaptateur d’itérateur qui décrit un objet itérateur inverse qui se comporte comme un itérateur d’accès aléatoire ou bidirectionnel, uniquement en sens inverse. Elle permet de parcourir une plage à reculons.

## <a name="syntax"></a>Syntaxe

```cpp
template <class RandomIterator>
class reverse_iterator
```

### <a name="parameters"></a>Paramètres

RandomIterator type qui représente l’itérateur à adapter pour fonctionner en sens inverse.

## <a name="remarks"></a>Notes

Les conteneurs fournis dans la bibliothèque standard C++ définissent également les types `reverse_iterator` et `const_reverse_iterator`, et possèdent les fonctions membres `rbegin` et `rend` qui retournent des itérateurs inverses. Ces itérateurs ont une sémantique de remplacement. L' `reverse_iterator` adaptateur complète cette fonctionnalité car il offre une sémantique d’insertion et peut également être utilisé avec des flux.

Le `reverse_iterator` qui requiert un itérateur bidirectionnel ne doit appeler aucune des fonctions membres,,, `operator+=` `operator+` `operator-=` `operator-` ou `operator[]` , qui peuvent uniquement être utilisées avec des itérateurs d’accès aléatoire.

La plage d’un itérateur est [*First*, *Last*), où le crochet de gauche indique l’inclusion de *First* et la parenthèse à droite indique l’inclusion des éléments jusqu’à l’exclusion de la *dernière* . Les mêmes éléments sont inclus dans la séquence inversée [ **Rev**  -  *First*, **Rev**  -  *Last*), de sorte que si *Last* est l’élément de fin d’une séquence, le premier élément **Rev**  -  *First* dans la séquence inversée pointe vers \* (*Last* -1). L'identité qui associe tous les itérateurs inverses à leurs itérateurs sous-jacents est :

&\*( **reverse_iterator** ( *i* )) = = &\* ( *i* -1).

En pratique, cela signifie que dans la séquence inversée le reverse_iterator se rapportera à l'élément situé une position au-delà (à droite) de l'élément auquel l'itérateur se rapportait dans la séquence d'origine. Ainsi, si un itérateur se rapportait à l'élément 6 dans la séquence (2, 4, 6, 8), le `reverse_iterator` se rapporte à l'élément 4 dans la séquence inversée (8, 6, 4, 2).

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[reverse_iterator](#reverse_iterator)|Construit un `reverse_iterator` par défaut ou un `reverse_iterator` à partir d'un itérateur sous-jacent.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[difference_type](#difference_type)|Type qui fournit la différence entre deux objets `reverse_iterator` se rapportant à des éléments dans le même conteneur.|
|[iterator_type](#iterator_type)|Type qui fournit l'itérateur sous-jacent d'un `reverse_iterator`.|
|[dirigé](#pointer)|Type qui fournit un pointeur vers un élément traité par un `reverse_iterator`.|
|[reference](#reference)|Type qui fournit une référence à un élément traité par un `reverse_iterator`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[base](#base)|Récupère l'itérateur sous-jacent à partir de son `reverse_iterator`.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator_star](#op_star)|Retourne l'élément traité par `reverse_iterator`.|
|[opérateur +](#op_add)|Ajoute un décalage à un itérateur et retourne le nouvel `reverse_iterator` qui se rapporte à l'élément inséré à la nouvelle position décalée.|
|[opérateur + +](#op_add_add)|Incrémente le `reverse_iterator` à l'élément suivant.|
|[opérateur + =](#op_add_eq)|Ajoute un décalage spécifié à partir d'un `reverse_iterator`.|
|[and](#operator-)|Soustrait un décalage à un `reverse_iterator` et retourne un `reverse_iterator` se rapportant à l'élément situé à la position décalée.|
|[opérateur--](#operator--)|Décrémente le `reverse_iterator` à l'élément précédent.|
|[opérateur =](#operator-_eq)|Soustrait un décalage spécifié d'un `reverse_iterator`.|
|[>Operator ](#op-arrow)|Retourne un pointeur vers l'élément traité par le `reverse_iterator`.|
|[operator&#91;&#93;](#op_at)|Retourne une référence à un élément décalé d'un nombre donné de positions par rapport à l'élément auquel un `reverse_iterator` se rapportait.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<iterator>

**Espace de noms :** std

## <a name="reverse_iteratorbase"></a><a name="base"></a> reverse_iterator :: base

Récupère l'itérateur sous-jacent à partir de son `reverse_iterator`.

```cpp
RandomIterator base() const;
```

### <a name="return-value"></a>Valeur renvoyée

Itérateur sous-jacent à `reverse_iterator`.

### <a name="remarks"></a>Notes

L’identité qui associe tous les itérateurs inverses à leurs itérateurs sous-jacents est :

&\*( `reverse_iterator` ( *i* )) = = &\* ( *i* -1).

En pratique, cela signifie que dans la séquence inversée, `reverse_iterator` se rapporte à l’élément situé une position à droite de l’élément auquel l’itérateur se rapportait dans la séquence d’origine. Ainsi, si un itérateur se rapportait à l'élément 6 dans la séquence (2, 4, 6, 8), le `reverse_iterator` se rapporte à l'élément 4 dans la séquence inversée (8, 6, 4, 2).

### <a name="example"></a>Exemple

```cpp
// reverse_iterator_base.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos, bpos;
   pos = find ( vec.begin ( ), vec.end ( ), 6 );
   cout << "The iterator pos points to: " << *pos << "." << endl;

   typedef reverse_iterator<vector<int>::iterator>::iterator_type it_vec_int_type;

   reverse_iterator<it_vec_int_type> rpos ( pos );
   cout << "The reverse_iterator rpos points to: " << *rpos
        << "." << endl;

   bpos = rpos.base ( );
   cout << "The iterator underlying rpos is bpos & it points to: "
        << *bpos << "." << endl;
}
```

## <a name="reverse_iteratordifference_type"></a><a name="difference_type"></a> reverse_iterator ::d ifference_type

Type qui fournit la différence entre deux objets `reverse_iterator` se rapportant à des éléments dans le même conteneur.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type  difference_type;
```

### <a name="remarks"></a>Notes

Le type de différence entre objets `reverse_iterator` est le même que le type de différence entre itérateurs.

Le type est un synonyme de la caractéristique d’itérateur TypeName `iterator_traits` \< **RandomIterator**> **::p ointer**.

### <a name="example"></a>Exemple

Consultez [reverse_iterator::operator&#91;&#93;](#op_at) pour obtenir un exemple montrant comment déclarer et utiliser `difference_type`.

## <a name="reverse_iteratoriterator_type"></a><a name="iterator_type"></a> reverse_iterator :: iterator_type

Type qui fournit l'itérateur sous-jacent d'un `reverse_iterator`.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Iterator`.

### <a name="example"></a>Exemple

Consultez [reverse_iterator::base](#base) pour obtenir un exemple montrant comment déclarer et utiliser `iterator_type`.

## <a name="reverse_iteratoroperator"></a><a name="op_star"></a> reverse_iterator ::, opérateur\*

Retourne l’élément traité par un reverse_iterator.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur des éléments traités par le reverse_iterator.

### <a name="remarks"></a>Notes

L’opérateur retourne \* ( **Current** -1).

### <a name="example"></a>Exemple

```cpp
// reverse_iterator_op_ref.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos, bpos;
   pos = find ( vec.begin ( ), vec.end ( ), 6 );

   // Declare a difference type for a parameter
   // declare a reference return type
   reverse_iterator<vector<int>::iterator>::reference refpos = *pos;
   cout << "The iterator pos points to: " << refpos << "." << endl;
}
```

## <a name="reverse_iteratoroperator"></a><a name="op_add"></a> reverse_iterator :: Operator +

Ajoute un décalage à un itérateur et retourne le nouvel `reverse_iterator` qui se rapporte à l'élément inséré à la nouvelle position décalée.

```cpp
reverse_iterator<RandomIterator> operator+(difference_type Off) const;
```

### <a name="parameters"></a>Paramètres

*Préférable*\
Décalage à ajouter à l’itérateur inverse.

### <a name="return-value"></a>Valeur renvoyée

`reverse_iterator` se rapportant à l’élément de décalage.

### <a name="remarks"></a>Notes

Cette fonction membre peut uniquement être utilisée si le `reverse_iterator` remplit les conditions pour un itérateur d’accès aléatoire.

### <a name="example"></a>Exemple

```cpp
// reverse_iterator_op_add.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   vector <int>::reverse_iterator rVPOS2 =rVPOS1 + 2; // offset added
   cout << "After the +2 offset, the iterator rVPOS2 points\n"
        << " to the 3rd element in the reversed sequence: "
        << *rVPOS2 << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 10.
After the +2 offset, the iterator rVPOS2 points
to the 3rd element in the reversed sequence: 6.
```

## <a name="reverse_iteratoroperator"></a><a name="op_add_add"></a> reverse_iterator :: Operator + +

Incrémente le reverse_iterator à l’élément précédent.

```cpp
reverse_iterator<RandomIterator>& operator++();
reverse_iterator<RandomIterator> operator++(int);
```

### <a name="return-value"></a>Valeur renvoyée

Le premier opérateur retourne le `reverse_iterator` préincrémenté et le deuxième, l’opérateur de postincrémentation, retourne une copie du `reverse_iterator` incrémenté.

### <a name="remarks"></a>Notes

Cette fonction membre peut uniquement être utilisée si le `reverse_iterator` remplit les conditions pour un itérateur bidirectionnel.

### <a name="example"></a>Exemple

```cpp
// reverse_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i - 1 );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1++;  // postincrement, preincrement: ++rVPSO1

   cout << "After incrementing, the iterator rVPOS1 points\n"
        << " to the second element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 1 3 5 7 9 ).
The vector vec reversed is: ( 9 7 5 3 1 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 9.
After incrementing, the iterator rVPOS1 points
to the second element in the reversed sequence: 7.
```

## <a name="reverse_iteratoroperator"></a><a name="op_add_eq"></a> reverse_iterator :: Operator + =

Ajoute un décalage spécifié à partir d’un reverse_iterator.

```cpp
reverse_iterator<RandomIterator>& operator+=(difference_type Off);
```

### <a name="parameters"></a>Paramètres

*Préférable*\
Décalage d’incrémentation de l’itérateur.

### <a name="return-value"></a>Valeur renvoyée

Référence à l’élément traité par le `reverse_iterator`.

### <a name="example"></a>Exemple

```cpp
// reverse_iterator_op_addoff.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1+=2;   // addition of an offset
   cout << "After the +2 offset, the iterator rVPOS1 now points\n"
        << " to the third element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 10.
After the +2 offset, the iterator rVPOS1 now points
to the third element in the reversed sequence: 6.
```

## <a name="reverse_iteratoroperator-"></a><a name="operator-"></a> reverse_iterator :: Operator-

Soustrait un décalage à un `reverse_iterator` et retourne un `reverse_iterator` se rapportant à l'élément situé à la position décalée.

```cpp
reverse_iterator<RandomIterator> operator-(difference_type Off) const;
```

### <a name="parameters"></a>Paramètres

*Préférable*\
Décalage à soustraire du reverse_iterator.

### <a name="return-value"></a>Valeur renvoyée

`reverse_iterator` se rapportant à l’élément de décalage.

### <a name="remarks"></a>Notes

Cette fonction membre peut uniquement être utilisée si le `reverse_iterator` remplit les conditions pour un itérateur d’accès aléatoire.

### <a name="example"></a>Exemple

```cpp
// reverse_iterator_op_sub.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 3 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   vector <int>::reverse_iterator rVPOS2 =rVPOS1 - 2; // offset subtracted
   cout << "After the -2 offset, the iterator rVPOS2 points\n"
        << " to the 2nd element from the last in the reversed sequence: "
        << *rVPOS2 << "." << endl;
}
```

```Output
The vector vec is: ( 3 6 9 12 15 ).
The vector vec reversed is: ( 15 12 9 6 3 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 3.
After the -2 offset, the iterator rVPOS2 points
to the 2nd element from the last in the reversed sequence: 9.
```

## <a name="reverse_iteratoroperator--"></a><a name="operator--"></a> reverse_iterator :: Operator--

Décrémente le reverse_iterator à l’élément précédent.

```cpp
reverse_iterator<RandomIterator>& operator--();
reverse_iterator<RandomIterator> operator--(int);
```

### <a name="return-value"></a>Valeur renvoyée

Le premier opérateur retourne le `reverse_iterator` prédécrémenté et le deuxième, l’opérateur de postdécrémentation, retourne une copie du `reverse_iterator` décrémenté.

### <a name="remarks"></a>Notes

Cette fonction membre peut uniquement être utilisée si le `reverse_iterator` remplit les conditions pour un itérateur bidirectionnel.

### <a name="example"></a>Exemple

```cpp
// reverse_iterator_op_decr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i - 1 );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;
   rVPOS1--;  // postdecrement, predecrement: --rVPSO1

   cout << "After the decrement, the iterator rVPOS1 points\n"
        << " to the next-to-last element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 1 3 5 7 9 ).
The vector vec reversed is: ( 9 7 5 3 1 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 1.
After the decrement, the iterator rVPOS1 points
to the next-to-last element in the reversed sequence: 3.
```

## <a name="reverse_iteratoroperator-"></a><a name="operator-_eq"></a> reverse_iterator :: Operator-=

Soustrait un décalage spécifié d'un `reverse_iterator`.

```cpp
reverse_iterator<RandomIterator>& operator-=(difference_type Off);
```

### <a name="parameters"></a>Paramètres

*Préférable*\
Décalage à soustraire du `reverse_iterator`.

### <a name="remarks"></a>Notes

Cette fonction membre peut uniquement être utilisée si le `reverse_iterator` remplit les conditions pour un itérateur d’accès aléatoire.

L’opérateur évalue **actuellement**  +  *off* , puis retourne **\* This**.

### <a name="example"></a>Exemple

```cpp
// reverse_iterator_op_suboff.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 3 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1-=2;      // Subtraction of an offset
   cout << "After the -2 offset, the iterator rVPOS1 now points\n"
        << " to the 2nd element from the last in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 3 6 9 12 15 ).
The vector vec reversed is: ( 15 12 9 6 3 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 3.
After the -2 offset, the iterator rVPOS1 now points
to the 2nd element from the last in the reversed sequence: 9.
```

## <a name="reverse_iteratoroperator-gt"></a><a name="op-arrow"></a> reverse_iterator :: Operator-&gt;

Retourne un pointeur vers l'élément traité par le `reverse_iterator`.

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’élément ciblé par le `reverse_iterator`.

### <a name="remarks"></a>Notes

L’opérateur retourne **& \* \* This**.

### <a name="example"></a>Exemple

```cpp
// reverse_iterator_ptrto.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

int main( )
{
   using namespace std;

   typedef vector<pair<int,int> > pVector;
   pVector vec;
   vec.push_back(pVector::value_type(1,2));
   vec.push_back(pVector::value_type(3,4));
   vec.push_back(pVector::value_type(5,6));

   pVector::iterator pvIter;
   cout << "The vector vec of integer pairs is:\n( ";
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";
   cout << ")" << endl << endl;

   pVector::reverse_iterator rpvIter;
   cout << "The vector vec reversed is:\n( ";
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++ )
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";
   cout << ")" << endl << endl;

   pVector::iterator pos = vec.begin ( );
   pos++;
   cout << "The iterator pos points to:\n( " << pos -> first << ", "
   << pos -> second << " )" << endl << endl;

   pVector::reverse_iterator rpos (pos);

   // Use operator -> with return type: why type int and not int*
   int fint = rpos -> first;
   int sint = rpos -> second;

   cout << "The reverse_iterator rpos points to:\n( " << fint << ", "
   << sint << " )" << endl;
}
```

```Output
The vector vec of integer pairs is:
( ( 1, 2) ( 3, 4) ( 5, 6) )

The vector vec reversed is:
( ( 5, 6) ( 3, 4) ( 1, 2) )

The iterator pos points to:
( 3, 4 )

The reverse_iterator rpos points to:
( 1, 2 )
```

## <a name="reverse_iteratoroperator"></a><a name="op_at"></a> reverse_iterator :: Operator []

Retourne une référence à un élément décalé d'un nombre donné de positions par rapport à l'élément auquel un `reverse_iterator` se rapportait.

```cpp
reference operator[](difference_type Off) const;
```

### <a name="parameters"></a>Paramètres

*Préférable*\
Décalage par rapport au `reverse_iterator` traité.

### <a name="return-value"></a>Valeur renvoyée

Référence au décalage de l’élément.

### <a name="remarks"></a>Notes

L’opérateur retourne <strong>\*</strong> ( **\* This**  +  `Off` ).

### <a name="example"></a>Exemple

```cpp
// reverse_iterator_ret_ref.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos;
   pos = find ( vec.begin ( ), vec.end ( ), 8 );
   reverse_iterator<vector<int>::iterator> rpos ( pos );

   // Declare a difference type for a parameter
   reverse_iterator<vector<int>::iterator>::difference_type diff = 2;

   cout << "The iterator pos points to: " << *pos << "." << endl;
   cout << "The iterator rpos points to: " << *rpos << "." << endl;

   // Declare a reference return type & use operator[]
   reverse_iterator<vector<int>::iterator>::reference refrpos = rpos [diff];
   cout << "The iterator rpos now points to: " << refrpos << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator pos points to: 8.
The iterator rpos points to: 6.
The iterator rpos now points to: 2.
```

## <a name="reverse_iteratorpointer"></a><a name="pointer"></a> reverse_iterator ::p ointer

Type qui fournit un pointeur vers un élément traité par un `reverse_iterator`.

```cpp
typedef typename iterator_traits<RandomIterator>::pointer pointer;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la caractéristique d’itérateur TypeName `iterator_traits` \< *RandomIterator*> **::p ointer**.

### <a name="example"></a>Exemple

```cpp
// reverse_iterator_pointer.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

int main( )
{
   using namespace std;

   typedef vector<pair<int,int> > pVector;
   pVector vec;
   vec.push_back( pVector::value_type( 1,2 ) );
   vec.push_back( pVector::value_type( 3,4 ) );
   vec.push_back( pVector::value_type( 5,6 ) );

   pVector::iterator pvIter;
   cout << "The vector vec of integer pairs is:\n" << "( ";
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";
   cout << ")" << endl;

   pVector::reverse_iterator rpvIter;
   cout << "\nThe vector vec reversed is:\n" << "( ";
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++)
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";
   cout << ")" << endl;

   pVector::iterator pos = vec.begin ( );
   pos++;
   cout << "\nThe iterator pos points to:\n"
        << "( " << pos -> first << ", "
        << pos -> second << " )" << endl;

   pVector::reverse_iterator rpos (pos);
   cout << "\nThe iterator rpos points to:\n"
        << "( " << rpos -> first << ", "
        << rpos -> second << " )" << endl;
}
```

```Output
The vector vec of integer pairs is:
( ( 1, 2) ( 3, 4) ( 5, 6) )

The vector vec reversed is:
( ( 5, 6) ( 3, 4) ( 1, 2) )

The iterator pos points to:
( 3, 4 )

The iterator rpos points to:
( 1, 2 )
```

## <a name="reverse_iteratorreference"></a><a name="reference"></a> reverse_iterator :: référence

Type qui fournit une référence à un élément traité par un reverse_iterator.

```cpp
typedef typename iterator_traits<RandomIterator>::reference reference;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la caractéristique d’itérateur TypeName `iterator_traits` \< *RandomIterator*> **:: Reference**.

### <a name="example"></a>Exemple

Consultez [reverse_iterator :: operator&#91;&#93;](#op_at) ou [reverse_iterator :: Operator *](#op_star) pour obtenir des exemples montrant comment déclarer et utiliser `reference` .

## <a name="reverse_iteratorreverse_iterator"></a><a name="reverse_iterator"></a> reverse_iterator :: reverse_iterator

Construit un `reverse_iterator` par défaut ou un `reverse_iterator` à partir d'un itérateur sous-jacent.

```cpp
reverse_iterator();
explicit reverse_iterator(RandomIterator right);

template <class Type>
reverse_iterator(const reverse_iterator<Type>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Itérateur devant être adapté à un `reverse_iterator`.

### <a name="return-value"></a>Valeur renvoyée

`reverse_iterator` par défaut ou `reverse_iterator` utilisé pour l’adaptation d’un itérateur sous-jacent.

### <a name="remarks"></a>Notes

L'identité qui associe tous les itérateurs inverses à leurs itérateurs sous-jacents est :

&\*( `reverse_iterator` ( *i* )) = = &\* ( *i* -1).

En pratique, cela signifie que dans la séquence inversée le reverse_iterator se rapportera à l'élément situé une position au-delà (à droite) de l'élément auquel l'itérateur se rapportait dans la séquence d'origine. Ainsi, si un itérateur se rapportait à l'élément 6 dans la séquence (2, 4, 6, 8), le `reverse_iterator` se rapporte à l'élément 4 dans la séquence inversée (8, 6, 4, 2).

### <a name="example"></a>Exemple

```cpp
// reverse_iterator_reverse_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos;
   pos = find ( vec.begin ( ), vec.end ( ), 4 );
   cout << "The iterator pos = " << *pos << "." << endl;

   vector <int>::reverse_iterator rpos ( pos );
   cout << "The reverse_iterator rpos = " << *rpos
        << "." << endl;
}
```

## <a name="see-also"></a>Voir aussi

[\<iterator>](../standard-library/iterator.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
