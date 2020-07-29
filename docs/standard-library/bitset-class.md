---
title: bitset, classe
ms.date: 03/27/2019
f1_keywords:
- bitset/std::bitset
- bitset/std::bitset::element_type
- bitset/std::bitset::all
- bitset/std::bitset::any
- bitset/std::bitset::count
- bitset/std::bitset::flip
- bitset/std::bitset::none
- bitset/std::bitset::reset
- bitset/std::bitset::set
- bitset/std::bitset::size
- bitset/std::bitset::test
- bitset/std::bitset::to_string
- bitset/std::bitset::to_ullong
- bitset/std::bitset::to_ulong
- bitset/std::bitset::reference
helpviewer_keywords:
- std::bitset [C++]
- std::bitset [C++], element_type
- std::bitset [C++], all
- std::bitset [C++], any
- std::bitset [C++], count
- std::bitset [C++], flip
- std::bitset [C++], none
- std::bitset [C++], reset
- std::bitset [C++], set
- std::bitset [C++], size
- std::bitset [C++], test
- std::bitset [C++], to_string
- std::bitset [C++], to_ullong
- std::bitset [C++], to_ulong
- std::bitset [C++], reference
ms.assetid: 28b86964-87b4-429c-8124-b6c251b6c50b
ms.openlocfilehash: 9a822e635ea3a1fd035a6a4b1d2b38250c96158a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217842"
---
# <a name="bitset-class"></a>bitset, classe

Décrit un type d'objet stockant une séquence composée d'un nombre fixe de bits qui offrent un moyen compact de conserver des indicateurs d'un ensemble d'éléments ou de conditions. La classe bitset prend en charge les opérations sur les objets de type bitset qui contiennent une collection de bits et qui fournissent un accès à délai constant à chaque bit.

## <a name="syntax"></a>Syntaxe

```cpp
template <size_t N>
class bitset
```

### <a name="parameters"></a>Paramètres

*N*\
Spécifie le nombre de bits dans l’objet BitSet avec un entier différent de zéro de type `size_t` qui doit être connu au moment de la compilation.

## <a name="remarks"></a>Notes

Contrairement à la [ \<bool> classe Vector](../standard-library/vector-bool-class.md)similaire, la classe BitSet n’a pas d’itérateurs et n’est pas un conteneur de bibliothèque standard C++. Elle diffère également de Vector \<bool> par une taille spécifique qui est fixée au moment de la compilation conformément à la taille spécifiée par le paramètre de modèle *N* lorsque le **BitSet \<N\> ** est déclaré.

Un bit est défini si sa valeur est 1, et est réinitialisé si sa valeur est 0. Basculer ou inverser un bit consiste à passer sa valeur de 1 à 0 ou de 0 à 1. Les *N* bits d’un bitset sont indexés par des valeurs entières allant de 0 à *N* - 1, où 0 indexe la position du premier bit et *N* - 1 la position du bit final.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|||
|-|-|
|[bitset](#bitset)|Construit un objet de la classe `bitset\<N>` et initialise les bits à zéro, à une valeur spécifiée ou à des valeurs obtenues auprès des caractères d'une chaîne.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[element_type](#element_type)|Type qui est un synonyme du type de données **`bool`** et qui peut être utilisé pour référencer les bits d’élément dans un `bitset` .|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[tous les](#all)|Teste tous les bits de ce `bitset` pour déterminer s’ils ont tous la valeur **`true`** .|
|[aux](#any)|La fonction membre teste si des bits de la séquence sont définis sur 1.|
|[count](#count)|La fonction membre retourne le nombre de bits définis dans la séquence de bits.|
|[flip](#flip)|Inverse la valeur de tous les bits d’un `bitset` ou inverse un seul bit à une position spécifiée.|
|[Aucune](#none)|Teste si aucun bit n'a été défini sur 1 dans un objet `bitset`.|
|[reset](#reset)|Réinitialise tous les bits d'un `bitset` à 0 ou réinitialise à 0 un bit à une position spécifiée.|
|[set](#set)|Définit tous les bits d'un `bitset` sur 1 ou définit sur 1 un bit à une position spécifiée.|
|[size](#size)|Retourne le nombre de bits d'un objet `bitset`.|
|[test](#test)|Teste si le bit à une position spécifiée d'un `bitset` est défini sur 1.|
|[to_string](#to_string)|Convertit un objet `bitset` en une représentation sous forme de chaîne.|
|[to_ullong](#to_ullong)|Retourne la somme des valeurs de bits dans le `bitset` en tant que **`unsigned long long`** .|
|[to_ulong](#to_ulong)|Convertit un `bitset` objet en **`unsigned long`** qui générerait la séquence de bits contenue s’il était utilisé pour initialiser le `bitset` .|

### <a name="classes"></a>Classes

|||
|-|-|
|[reference](#reference)|Classe proxy qui fournit des références aux bits contenus dans un `bitset` et qui est utilisée pour accéder aux bits individuels et pour s'en servir comme une classe d'assistance pour l'opérateur `operator[]` de la classe `bitset`.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur ! =](#op_neq)|Teste l'inégalité d'un `bitset` cible avec un `bitset` spécifié.|
|[&opérateur =](#op_and_eq)|Effectue une combinaison au niveau du bit de bitsets avec l'opération `AND` logique.|
|[<<d’opérateur](#op_lshift)|Décale les bits d'un `bitset` vers la gauche d'un nombre spécifié de positions et retourne le résultat dans un nouveau `bitset`.|
|[<<opérateur =](#op_lshift_eq)|Décale les bits d'un `bitset` vers la gauche d'un nombre spécifié de positions et retourne le résultat dans le `bitset` ciblé.|
|[opérateur = =](#op_eq_eq)|Teste l'égalité d'un `bitset` cible avec un `bitset` spécifié.|
|[>>d’opérateur](#op_rshift)|Décale les bits d'un `bitset` vers la droite d'un nombre spécifié de positions et retourne le résultat dans un nouveau `bitset`.|
|[>>opérateur =](#op_rshift_eq)|Décale les bits d'un `bitset` vers la droite d'un nombre spécifié de positions et retourne le résultat dans le `bitset` ciblé.|
|[operator&#91;&#93;](#op_at)|Retourne une référence à un bit à une position spécifiée d'un `bitset` si le `bitset` est modifiable ; sinon, retourne la valeur du bit à cette position.|
|[opérateur ^ =](#op_xor_eq)|Effectue une combinaison au niveau du bit de bitsets avec l'opération `OR` exclusive.|
|[&#124;opérateur =](#op_or_eq)|Effectue une combinaison au niveau du bit de bitsets avec l'opération `OR` inclusive.|
|[~, opérateur](#op_not)|Inverse tous les bits d’un `bitset` cible et retourne le résultat.|

### <a name="structures"></a>Structures

|||
|-|-|
|[hash](#hash)||

### <a name="all"></a><a name="all"></a>tous les

Teste tous les bits de ce bitset pour déterminer s'ils ont la valeur true.

```cpp
bool all() const;
```

#### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si tous les bits de ce bitset ont la valeur true. Retourne **`false`** si un ou plusieurs bits ont la valeur false.

### <a name="any"></a><a name="any"></a>aux

Vérifie si des bits de la séquence sont définis sur 1.

```cpp
bool any() const;
```

#### <a name="return-value"></a>Valeur de retour

**`true`** Si un bit de BitSet a la valeur 1 ; **`false`** si tous les bits sont 0.

#### <a name="example"></a>Exemple

```cpp
// bitset_any.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "The original bitset b1( 6 ) is: ( "<< b1 << " )"
        << endl;

   b = b1.any ( );

   if ( b )
      cout << "At least one of the bits in bitset is set to 1."
           << endl;
   else
      cout << "None of the bits in bitset are set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );

   cout << "The reset bitset is: ( "<< b1 << " )"
        << endl;

   rb = rb1.any ( );

   if ( rb )
      cout << "At least one of the bits in the reset bitset "
           << "are set to 1." << endl;
   else
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
}
```

```Output
The original bitset b1( 6 ) is: ( 00110 )
At least one of the bits in bitset is set to 1.
The reset bitset is: ( 00000 )
None of the bits in bitset b1 are set to 1.
```

### <a name="bitset"></a><a name="bitset"></a>BitSet

Construit un objet de la classe `bitset\<N>` et initialise les bits avec la valeur zéro, une valeur spécifiée ou des valeurs obtenues à partir des caractères d’une chaîne.

```cpp
bitset();

bitset(
    unsigned long long val);

explicit bitset(
    const char* _CStr);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos = 0);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos,
    typename basic_string<CharType, Traits, Allocator>::size_type count,
    CharType _Zero = CharType ('0'),
    CharType _One = CharType ('1'));
```

#### <a name="parameters"></a>Paramètres

*multiples*\
Entier non signé dont la représentation de base 2 est utilisée pour initialiser les bits du bitset en cours de construction.

*Str*\
Chaîne composée de valeurs zéro et un utilisée pour initialiser les valeurs de bit du bitset.

*_CStr*\
Chaîne de style C composées de valeurs zéro et un utilisée pour initialiser les valeurs de bit du bitset.

*_Pos*\
Position du caractère dans la chaîne, en comptant de gauche à droite à partir de zéro, utilisée pour initialiser le premier bit du bitset.

*saut*\
Nombre de caractères dans la chaîne utilisée pour fournir les valeurs initiales des bits du bitset.

*_Zero*\
Caractère utilisé pour représenter la valeur zéro. La valeur par défaut est « 0 ».

*_One*\
Caractère utilisé pour représenter la valeur un. La valeur par défaut est « 1 ».

#### <a name="remarks"></a>Notes

Trois constructeurs peuvent être utilisés pour construire des objets de classe `bitset\<N>` :

- Le premier constructeur n’accepte aucun paramètre, construit un objet de classe `bitset\<N>` et initialise tous les N bits avec la valeur par défaut zéro.

- Le deuxième constructeur construit un objet de classe `bitset\<N>` et initialise les bits à l’aide du paramètre unique **`unsigned long long`** .

- Le troisième constructeur construit un objet de classe `bitset\<N>`, en initialisant les N bits avec des valeurs qui correspondent aux caractères fournis dans une chaîne de caractères de style C composées de valeurs zéro et un. Vous appelez le constructeur sans caster la chaîne en type de chaîne : `bitset<5> b5("01011");`

Deux modèles de constructeur sont également fournis :

- Le premier modèle constructeur construit un objet de classe `bitset\<N>` et initialise les bits à partir des caractères fournis dans une chaîne composée de valeurs zéro et un. Si les caractères de la chaîne sont différents de 0 ou 1, le constructeur lève un objet de la classe [invalid argument](../standard-library/invalid-argument-class.md). Si la position spécifiée (*_Pos*) est au-delà de la longueur de la chaîne, le constructeur lève un objet de la classe [out_of_range](../standard-library/out-of-range-class.md). Le constructeur définit uniquement les bits à la position *j* du bitset pour lesquels le caractère de la chaîne à la position `_Pos + j` est 1. Par défaut, *_Pos* a la valeur 0.

- Le deuxième modèle de constructeur est similaire au premier, mais il comprend un paramètre supplémentaire (*Count*) qui est utilisé pour spécifier le nombre de bits à initialiser. Il possède également deux paramètres facultatifs, *_Zero* et *_One*, qui indiquent le caractère de la *chaîne* à interpréter pour signifier un bit 0 et un bit 1, respectivement.

#### <a name="example"></a>Exemple

```cpp
// bitset_bitset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   // Using the default constructor
   using namespace std;
   bitset<2> b0;
   cout << "The set of bits in bitset<2> b0 is: ( "
        << b0 << " )." << endl;

   // Using the second member function
   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1( 6 ) is: ( "
        << b1 << " )." << endl;

   // The template parameter N can be an expresssion
   bitset< 2 * sizeof ( int ) > b2;
   cout << "The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( "
        << b2 << " )." << endl;

   // The base two representation will be truncated
   // if its length exceeds the size of the bitset
   bitset<3> b3 ( 6 );
   cout << "The set of bits in bitset<3> b3( 6 ) is ( "
        << b3 << " )." << endl;

   // Using a c-style string to initialize the bitset
    bitset<7> b3andahalf ( "1001001" );
    cout << "The set of bits in bitset<7> b3andahalf ( \"1001001\" )"
         << " is ( " << b3andahalf << " )." << endl;

   // Using the fifth member function with the first parameter
   string bitval4 ( "10011" );
   bitset<5> b4 ( bitval4 );
   cout << "The set of bits in bitset<5> b4( bitval4 ) is ( "
        << b4 << " )." << endl;

   // Only part of the string may be used for initialization

   // Starting at position 3 for a length of 6 (100110)
   string bitval5 ("11110011011");
   bitset<6> b5 ( bitval5, 3, 6 );
   cout << "The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( "
        << b5 << " )." << endl;

   // The bits not initialized with part of the string
   // will default to zero
   bitset<11> b6 ( bitval5, 3, 5 );
   cout << "The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( "
        << b6 << " )." << endl;

   // Starting at position 2 and continue to the end of the string
   bitset<9> b7 ( bitval5, 2 );
   cout << "The set of bits in bitset<9> b7( bitval, 2 ) is ( "
        << b7 << " )." << endl;
}
```

```Output
The set of bits in bitset<2> b0 is: ( 00 ).
The set of bits in bitset<5> b1( 6 ) is: ( 00110 ).
The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( 00000000 ).
The set of bits in bitset<3> b3( 6 ) is ( 110 ).
The set of bits in bitset<5> b4( bitval4 ) is ( 10011 ).
The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( 100110 ).
The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( 00000010011 ).
The set of bits in bitset<9> b7( bitval, 2 ) is ( 110011011 ).
```

### <a name="count"></a><a name="count"></a>saut

Retourne le nombre de bits définis dans la séquence de bits.

```cpp
size_t count() const;
```

#### <a name="return-value"></a>Valeur de retour

Nombre de bits définis dans la séquence de bits.

#### <a name="example"></a>Exemple

```cpp
// bitset_count.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
    using namespace std;

    bitset<5> b1(4);

    cout << "The collection of bits in the original bitset is: ( "
         << b1 << " )" << endl;

    size_t i;
    i = b1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << i << "." << endl;

    bitset<5> fb1;
    fb1 = b1.flip();

    cout << "The collection of flipped bits in the modified bitset "
         << "is: ( " << b1 << " )" << endl;

    size_t ii;
    ii = fb1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << ii << "." << endl;
}
```

```Output
The collection of bits in the original bitset is: ( 00100 )
The number of bits in the bitset set to 1 is: 1.
The collection of flipped bits in the modified bitset is: ( 11011 )
The number of bits in the bitset set to 1 is: 4.
```

### <a name="element_type"></a><a name="element_type"></a>element_type

Type qui est un synonyme du type de données **`bool`** et qui peut être utilisé pour référencer des bits d’élément dans un BitSet.

```cpp
typedef bool element_type;
```

#### <a name="example"></a>Exemple

```cpp
// bitset_elem_type.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<3> b1 ( 2 );
   cout << "Original bitset b1(6) is: ( "<< b1 << " )"
        << endl;

   //Compare two ways to reference bits in a bitset
   bool b;
   bitset<5>::element_type e;

   b = b1.test ( 2 );
   if ( b )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
   b1[2] = 1;
   cout << "Bitset b1 modified by b1[2] = 1 is: ( "<< b1 << " )"
        << endl;

   e = b1.test ( 2 );
   if ( e )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
}
```

```Output
Original bitset b1(6) is: ( 010 )
The bit at position 2 of bitset b1has a value of 0.
Bitset b1 modified by b1[2] = 1 is: ( 110 )
The bit at position 2 of bitset b1has a value of 1.
```

### <a name="flip"></a><a name="flip"></a>livre

Inverse la valeur de tous les bits d’un bitset ou inverse un seul bit à une position spécifiée.

```cpp
bitset\<N>& flip();
bitset\<N>& flip(size_t _Pos);
```

#### <a name="parameters"></a>Paramètres

*_Pos*\
Position du bit dont la valeur doit être inversée.

#### <a name="return-value"></a>Valeur de retour

Copie du bitset modifié pour lequel la fonction membre a été appelée.

#### <a name="remarks"></a>Notes

La deuxième fonction membre lève une exception [out_of_range](../standard-library/out-of-range-class.md) si la position spécifiée comme paramètre est supérieure à la taille *N* du **BitSet \<** *N* **> ** dont le bit a été inversé.

#### <a name="example"></a>Exemple

```cpp
// bitset_flip.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 6 );

   cout << "The collection of bits in the original bitset is: ( "
        << b1 << " )" << endl;

   bitset<5> fb1;
   fb1 = b1.flip ( );

   cout << "After flipping all the bits, the bitset becomes: ( "
        << fb1 << " )" << endl;

   bitset<5> f3b1;
   f3b1 = b1.flip ( 3 );

   cout << "After flipping the fourth bit, the bitset becomes: ( "
        << f3b1 << " )" << endl << endl;

   bitset<5> b2;
   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b2.flip(i);
      cout << b2 << "  The bit flipped is in position "
           << i << ".\n";
   }
}
```

```Output
The collection of bits in the original bitset is: ( 00110 )
After flipping all the bits, the bitset becomes: ( 11001 )
After flipping the fourth bit, the bitset becomes: ( 10001 )

00001  The bit flipped is in position 0.
00011  The bit flipped is in position 1.
00111  The bit flipped is in position 2.
01111  The bit flipped is in position 3.
11111  The bit flipped is in position 4.
```

### <a name="hash"></a><a name="hash"></a>format

```cpp
template <class T> struct hash;
template <size_t N> struct hash<bitset<N>>;
```

### <a name="none"></a><a name="none"></a>None

Vérifie si aucun bit n’a été défini sur 1 dans un objet bitset.

```cpp
bool none() const;
```

#### <a name="return-value"></a>Valeur de retour

**`true`** Si aucun bit de BitSet n’a été défini sur 1 ; **`false`** si au moins un bit a été défini sur 1.

#### <a name="example"></a>Exemple

```cpp
// bitset_none.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "Original bitset b1(6) is: ( " << b1 << " )"
        << endl;

   b = b1.none ( );

   if ( b )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );
   rb = rb1.none ( );
   if ( rb )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;
}
```

```Output
Original bitset b1(6) is: ( 00110 )
At least one of the bits in bitset b1 is set to 1.
None of the bits in bitset b1 are set to 1.
```

### <a name="operator"></a><a name="op_neq"></a>opérateur ! =

Vérifie si un bitset cible n’est pas égal à un bitset spécifié.

```cpp
bool operator!=(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>Paramètres

*Oui*\
Bitset à comparer au bitset cible pour vérifier leur inégalité.

#### <a name="return-value"></a>Valeur de retour

**`true`** Si les bitsets sont différents ; **`false`** s’ils sont identiques.

#### <a name="remarks"></a>Notes

Les bitsets doivent avoir la même taille pour pouvoir être comparés par la fonction d’opérateur membre.

#### <a name="example"></a>Exemple

```cpp
// bitset_op_NE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 != b2 )
      cout << "Bitset b1 is different from bitset b2." << endl;
   else
      cout << "Bitset b1 is the same as bitset b2." << endl;

   if ( b1 != b3 )
      cout << "Bitset b1 is different from bitset b3." << endl;
   else
      cout << "Bitset b1 is the same as bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 != b4 )
   //   cout << "Bitset b1 is different from bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="operatoramp"></a><a name="op_and_eq"></a>and&amp;=

Effectue une combinaison au niveau du bit de bitsets avec l'opération `AND` logique.

```cpp
bitset\<N>& operator&=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Paramètres

*Oui*\
Bitset à combiner au niveau du bit avec le bitset cible.

#### <a name="return-value"></a>Valeur de retour

BitSet cible modifié qui résulte de l’opération au niveau du bit `AND` avec le BitSet spécifié en tant que paramètre.

#### <a name="remarks"></a>Notes

Deux bits combinés par l' `AND` opérateur retournent **`true`** si chaque bit a la valeur true ; sinon, leur combinaison retourne **`false`** .

Bitsets doit avoir la même taille pour être combiné au niveau du bit avec l' `AND` opérateur par la fonction d’opérateur membre.

#### <a name="example"></a>Exemple

```cpp
// bitset_op_bitwise.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 &= b2;
   cout << "After bitwise AND combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset is unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 &= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise AND combination,
the target bitset b1 becomes:   ( 00011 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="operator"></a><a name="op_lshift"></a>and\<\<

Décale les bits d’un bitset vers la gauche d’un nombre spécifié de positions et retourne le résultat dans un nouveau bitset.

```cpp
bitset\<N> operator<<(size_t _Pos) const;
```

#### <a name="parameters"></a>Paramètres

*_Pos*\
Nombre de positions vers la gauche duquel les bits du bitset doivent être décalés.

#### <a name="return-value"></a>Valeur de retour

Bitset modifié avec les bits décalés vers la gauche du nombre nécessaire de positions.

#### <a name="remarks"></a>Notes

La fonction d’opérateur membre retourne **BitSet**( ** \* This**) **<<= POS,** où [<<=](#op_lshift_eq) décale les bits d’un BitSet vers la gauche d’un nombre spécifié de positions et retourne le résultat dans le BitSet ciblé.

#### <a name="example"></a>Exemple

```cpp
// bitset_op_LS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << " the bitset b2 is: ( "<< b2 << " )."
        << endl;

   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << " the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

### <a name="operatorltlt"></a><a name="op_lshift_eq"></a>and&lt;&lt;=

Décale les bits d’un bitset vers la gauche d’un nombre spécifié de positions et retourne le résultat dans le bitset ciblé.

```cpp
bitset\<N>& operator<<=(size_t _Pos);
```

#### <a name="parameters"></a>Paramètres

*_Pos*\
Nombre de positions vers la gauche duquel les bits du bitset doivent être décalés.

#### <a name="return-value"></a>Valeur de retour

Bitset ciblé modifié avec les bits décalés vers la gauche du nombre nécessaire de positions.

#### <a name="remarks"></a>Notes

Si aucun élément n’existe pour décaler à la position, la fonction efface le bit en le définissant sur 0.

#### <a name="example"></a>Exemple

```cpp
// bitset_op_LSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;
   b1 <<= 2;
   cout << "After shifting the bits 2 positions to the left,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the target bitset b1 becomes: ( 11100 ).
```

### <a name="operator"></a><a name="op_eq_eq"></a>opérateur = =

Vérifie si un bitset cible est égal à un bitset spécifié.

```cpp
bool operator==(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>Paramètres

*Oui*\
Bitset à comparer au bitset cible pour vérifier leur égalité.

#### <a name="return-value"></a>Valeur de retour

**`true`** Si les bitsets sont identiques ; **`false`** si elles sont différentes.

#### <a name="remarks"></a>Notes

Les bitsets doivent avoir la même taille pour pouvoir être comparés par la fonction d’opérateur membre.

#### <a name="example"></a>Exemple

```cpp
// bitset_op_EQ.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 == b2 )
      cout << "Bitset b1 is the same as bitset b2." << endl;
   else
      cout << "Bitset b1 is different from bitset b2." << endl;

   if ( b1 == b3 )
      cout << "Bitset b1 is the same as bitset b3." << endl;
   else
      cout << "Bitset b1 is different from bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 == b4 )
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is different from bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="operatorgtgt"></a><a name="op_rshift"></a>and&gt;&gt;

Décale les bits d’un bitset vers la droite d’un nombre spécifié de positions et retourne le résultat dans un nouveau bitset.

```cpp
bitset\<N> operator>>(size_t _Pos) const;
```

#### <a name="parameters"></a>Paramètres

*_Pos*\
Nombre de positions vers la droite duquel les bits du bitset doivent être décalés.

#### <a name="return-value"></a>Valeur de retour

Nouveau bitset où les bits ont été décalés vers la droite du nombre nécessaire de positions par rapport au bitset ciblé.

#### <a name="example"></a>Exemple

```cpp
// bitset_op_RS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << "the bitset b2 is: ( "<< b2 << " )."
        << endl;
   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << "the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

```Output
The bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the bitset b2 is: ( 11100 ).
After shifting the bits 1 position to the right,
the bitset b3 is: ( 01110 ).
```

### <a name="operatorgtgt"></a><a name="op_rshift_eq"></a>and&gt;&gt;=

Décale les bits d’un bitset vers la droite d’un nombre spécifié de positions et retourne le résultat dans le bitset ciblé.

```cpp
bitset\<N>& operator>>=(size_t _Pos);
```

#### <a name="parameters"></a>Paramètres

*_Pos*\
Nombre de positions vers la droite duquel les bits du bitset doivent être décalés.

#### <a name="return-value"></a>Valeur de retour

Bitset ciblé modifié avec les bits décalés vers la droite du nombre nécessaire de positions.

#### <a name="remarks"></a>Notes

Si aucun élément n’existe pour décaler à la position, la fonction efface le bit en le définissant sur 0.

#### <a name="example"></a>Exemple

```cpp
// bitset_op_RSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 28 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;

   b1 >>= 2;
   cout << "After shifting the bits 2 positions to the right,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 11100 ).
After shifting the bits 2 positions to the right,
the target bitset b1 becomes: ( 00111 ).
```

### <a name="operator"></a><a name="op_at"></a>[], opérateur

Retourne une référence à un bit à une position spécifiée d’un bitset si le bitset est modifiable ; sinon, retourne la valeur du bit à cette position.

```cpp
bool operator[](size_t _Pos) const;
reference operator[](size_t _Pos);
```

#### <a name="parameters"></a>Paramètres

*_Pos*\
Position situant le bit dans le bitset.

#### <a name="remarks"></a>Notes

Lorsque vous définissez le [ \_ \_ \_ niveau de débogage](../standard-library/iterator-debug-level.md) d’un itérateur sur 1 ou 2 dans votre Build, une erreur d’exécution se produit dans votre exécutable si vous tentez d’accéder à un élément situé en dehors des limites du BitSet. Pour plus d’informations, consultez [Itérateurs vérifiés](../standard-library/checked-iterators.md).

#### <a name="example"></a>Exemple

```cpp
// bitset_op_REF.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bool b;
   bitset<5> b1 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;

   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b = b1[ i ];
      cout << "  The bit in position "
           << i << " is " << b << ".\n";
   }
}
```

### <a name="operator"></a><a name="op_xor_eq"></a>opérateur ^ =

Effectue une combinaison au niveau du bit de bitsets avec l'opération `OR` exclusive.

```cpp
bitset\<N>& operator^=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Paramètres

*Oui*\
Bitset à combiner au niveau du bit avec le bitset cible.

#### <a name="return-value"></a>Valeur de retour

Bitset cible modifié qui résulte de l’opération `OR` exclusive au niveau du bit avec le bitset spécifié comme paramètre.

#### <a name="remarks"></a>Notes

Deux bits combinés par l’opérateur **or** exclusif sont retournés **`true`** si au moins un des bits, mais pas les deux, est **`true`** ; sinon, leur combinaison retourne **`false`** .

Les bitsets doivent avoir la même taille pour pouvoir être combinés au niveau du bit avec l’opérateur `OR` exclusif par la fonction d’opérateur membre.

#### <a name="example"></a>Exemple

```cpp
// bitset_op_bitwiseOR.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 ^= b2;
   cout << "After bitwise exclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise exclusive OR combination,
the target bitset b1 becomes:   ( 01100 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="operator124"></a><a name="op_or_eq"></a>&#124;opérateur =

Effectue une combinaison au niveau du bit de bitsets avec l'opération `OR` inclusive.

```cpp
bitset\<N>& operator|=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Paramètres

*Oui*\
Bitset à combiner au niveau du bit avec le bitset cible.

#### <a name="return-value"></a>Valeur de retour

Bitset cible modifié qui résulte de l’opération `OR` inclusive au niveau du bit avec le bitset spécifié comme paramètre.

#### <a name="remarks"></a>Notes

Deux bits combinés par l’opérateur inclusif `OR` retournent **`true`** si au moins un des bits est **`true`** ; si les deux bits sont **`false`** , leur combinaison retourne **`false`** .

Les bitsets doivent avoir la même taille pour pouvoir être combinés au niveau du bit avec l’opérateur `OR` inclusif par la fonction d’opérateur membre.

#### <a name="example"></a>Exemple

```cpp
// bitset_op_BIO.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 |= b2;
   cout << "After bitwise inclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise inclusive OR combination,
the target bitset b1 becomes:   ( 01111 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="operator"></a><a name="op_not"></a>~, opérateur

Inverse tous les bits d’un bitset cible et retourne le résultat.

```cpp
bitset\<N> operator~() const;
```

#### <a name="return-value"></a>Valeur de retour

Bitset avec tous ses bits inversés par rapport au bitset ciblé.

#### <a name="example"></a>Exemple

```cpp
// bitset_op_invert.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <bitset>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2;
   b2 = ~b1;

   cout << "Bitset b1 is: ( "<< b1 << " )." << endl;
   cout << "Bitset b2 = ~b1 is: ( "<< b2 << " )." << endl;

   // These bits could also be flipped using the flip member function
   bitset<5> b3;
   b3 = b1.flip( );
   cout << "Bitset b3 = b1.flip( ) is: ( "<< b2 << " )." << endl;
}
```

```Output
Bitset b1 is: ( 00111 ).
Bitset b2 = ~b1 is: ( 11000 ).
Bitset b3 = b1.flip( ) is: ( 11000 ).
```

### <a name="reference"></a><a name="reference"></a>faire

Classe proxy qui fournit des références aux bits contenus dans un bitset et est utilisée pour accéder aux bits individuels et pour s’en servir comme classe d’assistance pour `operator[]` de la classe bitset.

```cpp
class reference {
   friend class bitset\<N>;
public:
   reference& operator=(bool val);
   reference& operator=(const reference& _Bitref);
   bool operator~() const;
   operator bool() const;
   reference& flip();
};
```

#### <a name="parameters"></a>Paramètres

*multiples*\
Valeur de l’objet de type **`bool`** à assigner à un bit dans un BitSet.

*_Bitref*\
Référence de la forme *x [ i ]* au bit à la position *i* dans le bitset *x*.

#### <a name="return-value"></a>Valeur de retour

Référence au bit dans le BitSet spécifié par la position d’argument pour les premier, deuxième et cinquième fonctions membres de référence de classe, et **`true`** ou **`false`** , pour refléter la valeur du bit modifié dans le BitSet pour les troisième et quatrième fonctions membres de référence de classe.

#### <a name="remarks"></a>Notes

La classe `reference` existe uniquement dans une classe d’assistance pour le bitset `operator[]`. La classe membre décrit un objet qui peut accéder à un bit individuel d’un bitset. Supposons que *b* soit un objet de type **`bool`** , des objets *x* et *y* de type **BitSet \<** *N* **> **et des positions valides *i* et *j* dans ce type d’objet. La notation *x [i]* référence le bit à la position *i* dans le bitset *x*. Les fonctions membres de la classe `reference` fournissent, dans l’ordre, les opérations suivantes :

|Opération|Définition|
|---------------|----------------|
|*x*[*i*] = *b*|Stocke la **`bool`** valeur *b* à la position de bit *i* dans BitSet *x*.|
|*x*[*i*] = *y*[*j*]|Stocke la valeur du bit *y*[ *j*] à la position de bit *i* dans le bitset *x*.|
|*b* = ~ *x*[*i*]|Stocke la valeur retournée du bit *x*[ *i*] dans **`bool`** *b*.|
|*b*  =  *x*[*i*]|Stocke la valeur du bit *x*[ *i*] dans **`bool`** *b*.|
|*x*[*i*]. `flip`( )|Restocke la valeur basculée du bit *x*[ *i*] à la position de bit *i* dans *x*.|

#### <a name="example"></a>Exemple

```cpp
// bitset_reference.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 2 );
   bitset<5> b2 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;
   cout << "The initialized bitset<5> b2( 6 ) is: ( "<< b2 << " )."
        << endl;

   // Example of x [i] = b storing bool b at bit position i
   // in bitset x
   b1[ 0 ] = true;
   cout << "The bitset<5> b1 with the bit at position 0 set to 1"
        << "is: ( "<< b1 << " )" << endl;

   // Example of x [i] = y [j] storing the bool value of the
   // bit at position j in bitset y at bit position i in bitset x
   b2 [4] = b1 [0];      // b1 [0] = true
   cout << "The bitset<5> b2 with the bit at position 4 set to the "
        << "value\nof the bit at position 0 of the bit in "
        << "bitset<5> b1 is: ( "<<  b2  << " )" << endl;

   // Example of b = ~x [i] flipping the value of the bit at
   // position i of bitset x and storing the value in an
   // object b of type bool
   bool b = ~b2 [4];      // b2 [4] = false
   if ( b )
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is false." << endl;

   // Example of b = x [i] storing the value of the bit at
   // position i of bitset x in the object b of type bool
   b = b2 [4];
   if ( b )
      cout << "The value of the object b = b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = b2 [4] "
           << "of type bool is false." << endl;

   // Example of x [i] . flip ( ) toggling the value of the bit at
   // position i of bitset x
   cout << "Before flipping the value of the bit at position 4 in "
        << "bitset b2,\nit is ( "<<  b2  << " )." << endl;
   b2 [4].flip( );
   cout << "After flipping the value of the bit at position 4 in "
        << "bitset b2,\nit becomes ( "<<  b2  << " )." << endl;
   bool c;
   c = b2 [4].flip( );
   cout << "After a second flip, the value of the position 4 "
        << "bit in b2 is now: " << c << ".";
}
```

```Output
The initialized bitset<5> b1( 2 ) is: ( 00010 ).
The initialized bitset<5> b2( 6 ) is: ( 00110 ).
The bitset<5> b1 with the bit at position 0 set to 1 is: ( 00011 )
The bitset<5> b2 with the bit at position 4 set to the value
of the bit at position 0 of the bit in bitset<5> b1 is: ( 10110 )
The value of the object b = ~b2 [4] of type bool is false.
The value of the object b = b2 [4] of type bool is true.
Before flipping the value of the bit at position 4 in bitset b2,
it is ( 10110 ).
After flipping the value of the bit at position 4 in bitset b2,
it becomes ( 00110 ).
After a second flip, the value of the position 4 bit in b2 is now: 1.
```

### <a name="reset"></a><a name="reset"></a>initialisation

Redéfinit tous les bits d’un bitset sur 0 ou redéfinit sur 0 un bit à une position spécifiée.

```cpp
bitset\<N>& reset();
bitset\<N>& reset(size_t _Pos);
```

#### <a name="parameters"></a>Paramètres

*_Pos*\
Position du bit dans le bitset à redéfinir sur 0.

#### <a name="return-value"></a>Valeur de retour

Copie du bitset pour lequel la fonction membre a été appelée.

#### <a name="remarks"></a>Notes

La deuxième fonction membre lève une exception [out_of_range](../standard-library/out-of-range-class.md) si la position spécifiée est supérieure à la taille du bitset.

#### <a name="example"></a>Exemple

```cpp
// bitset_reset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 13 );
   cout << "The set of bits in bitset<5> b1(13) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1r3;
   b1r3 = b1.reset( 2 );
   cout << "The collecion of bits obtained from resetting the\n"
        << "third bit of bitset b1 is: ( "<< b1r3 << " )"
        << endl;

   bitset<5> b1r;
   b1r = b1.reset( );
   cout << "The collecion of bits obtained from resetting all\n"
        << "the elements of the bitset b1 is: ( "<< b1r << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(13) is: ( 01101 )
The collecion of bits obtained from resetting the
third bit of bitset b1 is: ( 01001 )
The collecion of bits obtained from resetting all
the elements of the bitset b1 is: ( 00000 )
```

### <a name="set"></a><a name="set"></a>définie

Définit tous les bits d’un bitset sur 1 ou définit sur 1 un bit à une position spécifiée.

```cpp
bitset\<N>& set();

bitset\<N>& set(
    size_t _Pos,
    bool val = true);
```

#### <a name="parameters"></a>Paramètres

*_Pos*\
Position du bit dans le bitset à définir sur une valeur assignée.

*multiples*\
Valeur à assigner au bit à la position spécifiée.

#### <a name="return-value"></a>Valeur de retour

Copie du bitset pour lequel la fonction membre a été appelée.

#### <a name="remarks"></a>Notes

La deuxième fonction membre lève une exception [out_of_range](../standard-library/out-of-range-class.md) si la position spécifiée est supérieure à la taille du bitset.

#### <a name="example"></a>Exemple

```cpp
// bitset_set.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1(6) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1s0;
   b1s0 = b1.set( 0 );
   cout << "The collecion of bits obtained from setting the\n"
        << "zeroth bit of bitset b1 is: ( "<< b1s0 << " )"
        << endl;

   bitset<5> bs1;
   bs1 = b1.set( );
   cout << "The collecion of bits obtained from setting all the\n"
        << "elements of the bitset b1 is: ( "<< bs1 << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(6) is: ( 00110 )
The collecion of bits obtained from setting the
zeroth bit of bitset b1 is: ( 00111 )
The collecion of bits obtained from setting all the
elements of the bitset b1 is: ( 11111 )
```

### <a name="size"></a><a name="size"></a>corps

Retourne le nombre de bits dans un objet bitset.

```cpp
size_t size() const;
```

#### <a name="return-value"></a>Valeur de retour

Nombre de bits, *N*, dans un BitSet \<N> .

#### <a name="example"></a>Exemple

```cpp
// bitset_size.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main()
{
    using namespace std;

    bitset<5> b1(6);
    size_t i;

    cout << "The set of bits in bitset<5> b1( 6 ) is: ( "<< b1 << " )"
         << endl;

    i = b1.size();

    cout << "The number of bits in bitset b1 is: " << i << "."
         << endl;
}
```

```Output
The set of bits in bitset<5> b1( 6 ) is: ( 00110 )
The number of bits in bitset b1 is: 5.
```

### <a name="test"></a><a name="test"></a>test

Vérifie si le bit à une position spécifiée d’un bitset est défini sur 1.

```cpp
bool test(size_t _Pos) const;
```

#### <a name="parameters"></a>Paramètres

*_Pos*\
Position du bit dans le bitset dont la valeur doit être vérifiée.

#### <a name="return-value"></a>Valeur de retour

**`true`** Si le bit spécifié par la position de l’argument a la valeur 1 ; Sinon, **`false`** .

#### <a name="remarks"></a>Notes

La fonction membre lève un [out_of_range](../standard-library/out-of-range-class.md)

### <a name="to_string"></a><a name="to_string"></a>to_string

Convertit un objet BitSet en une représentation sous forme de chaîne.

```cpp
template <class charT = char, class traits = char_traits<charT>, class Allocator = allocator<charT> >
   basic_string<charT, traits, Allocator> to_string(charT zero = charT('0'), charT one = charT('1')) const;
```

#### <a name="return-value"></a>Valeur retournée

Objet String de la classe `basic_string` , où chaque bit défini dans le BitSet a un caractère correspondant de 1, et un caractère égal à 0 si le bit n’est pas défini.

#### <a name="example"></a>Exemple

```cpp
// bitset_to_string.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   string s1;
   s1 =  b1.template to_string<char,
   char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n  by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The string returned from the bitset b1
  by the member function to_string( ) is: 00111.
```

### <a name="to_ullong"></a><a name="to_ullong"></a>to_ullong

Retourne une **`unsigned long long`** valeur qui contient les mêmes bits que le contenu de l’objet BitSet.

```cpp
unsigned long long to_ullong() const;
```

#### <a name="return-value"></a>Valeur retournée

Retourne la somme des valeurs de bit de la séquence de bits sous forme de **`unsigned long long`** . Cette **`unsigned long long`** valeur recrée les mêmes bits de jeu s’ils sont utilisés pour initialiser un BitSet.

#### <a name="exceptions"></a>Exceptions

Lève une [overflow_error](overflow-error-class.md) objet si un bit de la séquence de bits a une valeur de bit qui ne peut pas être représentée comme une valeur de type **`unsigned long long`** .

#### <a name="remarks"></a>Notes

Retourne la somme des valeurs de bit de la séquence de bits sous forme de **`unsigned long long`** .

### <a name="to_ulong"></a><a name="to_ulong"></a>to_ulong

Convertit un objet BitSet en un entier qui générerait la séquence de bits contenue s’il était utilisé pour initialiser le BitSet.

```cpp
unsigned long to_ulong( ) const;
```

#### <a name="return-value"></a>Valeur retournée

Entier qui générerait les bits dans un BitSet s’ils sont utilisés dans l’initialisation du BitSet.

#### <a name="remarks"></a>Notes

L’application de la fonction membre retourne l’entier qui a la même séquence de 1 et 0 chiffres que ceux trouvés dans la séquence de bits contenus dans le BitSet.

La fonction membre lève une [overflow_error](overflow-error-class.md) objet si un bit de la séquence de bits a une valeur de bit qui ne peut pas être représentée comme une valeur de type **`unsigned long`** .

#### <a name="example"></a>Exemple

```cpp
// bitset_to_ulong.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   unsigned long int i;
   i = b1.to_ulong( );
   cout << "The integer returned from the bitset b1,"
        << "\n  by the member function to_long( ), that"
        << "\n  generated the bits as a base two number is: "
        << i << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The integer returned from the bitset b1,
  by the member function to_long( ), that
  generated the bits as a base two number is: 7.
```
