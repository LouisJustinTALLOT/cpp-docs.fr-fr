---
description: 'En savoir plus sur : classe istreambuf_iterator'
title: istreambuf_iterator, classe
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::istreambuf_iterator
- iterator/std::istreambuf_iterator::char_type
- iterator/std::istreambuf_iterator::int_type
- iterator/std::istreambuf_iterator::istream_type
- iterator/std::istreambuf_iterator::streambuf_type
- iterator/std::istreambuf_iterator::traits_type
- iterator/std::istreambuf_iterator::equal
helpviewer_keywords:
- std::istreambuf_iterator [C++]
- std::istreambuf_iterator [C++], char_type
- std::istreambuf_iterator [C++], int_type
- std::istreambuf_iterator [C++], istream_type
- std::istreambuf_iterator [C++], streambuf_type
- std::istreambuf_iterator [C++], traits_type
- std::istreambuf_iterator [C++], equal
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
ms.openlocfilehash: 221141f5dd97be80b6f13b677f4ed253d75e1054
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306727"
---
# <a name="istreambuf_iterator-class"></a>istreambuf_iterator, classe

Le modèle de classe istreambuf_iterator décrit un objet itérateur d’entrée qui extrait des éléments de caractère d’une mémoire tampon de flux d’entrée, à laquelle il accède via un objet qu’il stocke, de type pointeur vers `basic_streambuf` \< **CharType**, **Traits**> .

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType class Traits = char_traits <CharType>>
class istreambuf_iterator
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```

### <a name="parameters"></a>Paramètres

*CharType*\
Type qui représente le type de caractère pour istreambuf_iterator.

*Caractéristiques*\
Type qui représente le type de caractère pour istreambuf_iterator. Cet argument est facultatif et sa valeur par défaut est `char_traits` \< *CharType> . *

## <a name="remarks"></a>Notes

La classe istreambuf_iterator doit répondre aux exigences d’un itérateur d’entrée.

Après avoir construit ou incrémenté un objet de classe istreambuf_iterator avec un pointeur stocké non null, l’objet tente d’extraire et de stocker un objet de type *CharType* à partir du flux d’entrée associé. Toutefois, l'extraction peut être différée jusqu'à ce que l'objet soit déréférencé ou copié. Si l'extraction échoue, l'objet remplace le pointeur stocké par un pointeur null, créant ainsi un indicateur de fin de séquence.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[istreambuf_iterator](#istreambuf_iterator)|Construit un `istreambuf_iterator` qui est initialisé pour lire des caractères à partir du flux d'entrée.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type qui fournit le type de caractère de `ostreambuf_iterator`.|
|[int_type](#int_type)|Type qui fournit un type entier pour un `istreambuf_iterator`.|
|[istream_type](#istream_type)|Type qui fournit le type de flux de `istream_iterator`.|
|[streambuf_type](#streambuf_type)|Type qui fournit le type de flux de `istreambuf_iterator`.|
|[traits_type](../standard-library/istream-iterator-class.md#traits_type)|Type qui fournit le type de caractéristique de `istream_iterator`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[valeur](#equal)|Vérifie l'égalité de deux itérateurs de tampon de flux d'entrée.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[and](#op_star)|L'opérateur de suppression de référence retourne le caractère suivant du flux.|
|[opérateur + +](#op_add_add)|Retourne le caractère suivant du flux d'entrée ou copie l'objet avant de l'incrémenter et de retourner sa copie.|
|[>Operator ](#op_arrow)|Retourne la valeur d'un membre, le cas échéant.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<iterator>

**Espace de noms :** std

## <a name="istreambuf_iteratorchar_type"></a><a name="char_type"></a> istreambuf_iterator :: char_type

Type qui fournit le type de caractère de `ostreambuf_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle *CharType*.

### <a name="example"></a>Exemple

```cpp
// istreambuf_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="istreambuf_iteratorequal"></a><a name="equal"></a> istreambuf_iterator :: EQUAL

Teste l’équivalence de deux itérateurs de mémoire tampon de flux d’entrée.

```cpp
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
Itérateur pour lequel vérifier l’égalité.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les deux `istreambuf_iterator` s sont des itérateurs de fin de flux ou si aucun n’est un itérateur de fin de flux ; sinon, **`false`** .

### <a name="remarks"></a>Notes

Une plage est définie par `istreambuf_iterator` à la position actuelle et l’itérateur de fin de flux, mais étant donné que tous les itérateurs de flux non finis sont équivalents sous la `equal` fonction membre, il n’est pas possible de définir des sous-plages à l’aide de `istreambuf_iterator` s. Les opérateurs `==` et `!=` ont la même sémantique.

### <a name="example"></a>Exemple

```cpp
// istreambuf_iterator_equal.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "(Try the example: 'Hello world!'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   istreambuf_iterator<char> charReadIn1 ( cin );
   istreambuf_iterator<char> charReadIn2 ( cin );

   bool b1 = charReadIn1.equal ( charReadIn2 );

   if (b1)
      cout << "The iterators are equal." << endl;
   else
      cout << "The iterators are not equal." << endl;
}
```

## <a name="istreambuf_iteratorint_type"></a><a name="int_type"></a> istreambuf_iterator :: int_type

Type qui fournit un type entier pour un `istreambuf_iterator`.

```cpp
typedef typename traits_type::int_type int_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `Traits::int_type`.

### <a name="example"></a>Exemple

```cpp
// istreambuf_iterator_int_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;
   istreambuf_iterator<char>::int_type inttype1 = 100;
   cout << "The inttype1 = " << inttype1 << "." << endl;
}
/* Output:
The inttype1 = 100.
*/
```

## <a name="istreambuf_iteratoristream_type"></a><a name="istream_type"></a> istreambuf_iterator :: istream_type

Type qui fournit le type de flux de `istreambuf_iterator`.

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `basic_istream` \< **CharType**, **Traits**> .

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `istream_type`, consultez l’exemple relatif à [istreambuf_iterator](#istreambuf_iterator).

## <a name="istreambuf_iteratoristreambuf_iterator"></a><a name="istreambuf_iterator"></a> istreambuf_iterator :: istreambuf_iterator

Construit un istreambuf_iterator qui est initialisé pour lire des caractères à partir du flux d’entrée.

```cpp
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```

### <a name="parameters"></a>Paramètres

*strbuf*\
Mémoire tampon de flux d’entrée à laquelle le `istreambuf_iterator` est attaché.

*_Istr*\
Flux d’entrée auquel le `istreambuf_iterator` est attaché.

### <a name="remarks"></a>Notes

Le premier constructeur initialise le pointeur de mémoire tampon de flux d’entrée avec *strbuf*. Le deuxième constructeur initialise le pointeur de mémoire tampon de flux d’entrée avec *_Istr*. `rdbuf`, puis tente finalement d’extraire et de stocker un objet de type `CharType` .

### <a name="example"></a>Exemple

```cpp
// istreambuf_iterator_istreambuf_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Following declarations will not compile:
   istreambuf_iterator<char>::istream_type &istrm = cin;
   istreambuf_iterator<char>::streambuf_type *strmbf = cin.rdbuf( );

   cout << "(Try the example: 'Oh what a world!'\n"
      << " then an Enter key to insert into the output,\n"
      << " & use a ctrl-Z Enter key combination to exit): ";
   istreambuf_iterator<char> charReadIn ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with hyphen-separators
   replace_copy ( charReadIn , istreambuf_iterator<char>( ),
      charOut , ' ' , '-' );
}
```

## <a name="istreambuf_iteratoroperator"></a><a name="op_star"></a> istreambuf_iterator :: Operator *

L'opérateur de suppression de référence retourne le caractère suivant du flux.

```cpp
CharType operator*() const;
```

### <a name="return-value"></a>Valeur renvoyée

Caractère suivant dans le flux.

### <a name="example"></a>Exemple

```cpp
// istreambuf_iterator_operator_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;   //Put value of outpos equal to inpos
      ++inpos;
      ++outpos;
   }
}
```

## <a name="istreambuf_iteratoroperator"></a><a name="op_add_add"></a> istreambuf_iterator :: Operator + +

Retourne le caractère suivant du flux d'entrée ou copie l'objet avant de l'incrémenter et de retourner sa copie.

```cpp
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Valeur renvoyée

`istreambuf_iterator` ou une référence à un `istreambuf_iterator`.

### <a name="remarks"></a>Notes

Le premier opérateur tente finalement d’extraire et de stocker un objet de type `CharType` à partir du flux d’entrée associé. Le deuxième opérateur effectue une copie de l’objet, incrémente l’objet, puis retourne la copie.

### <a name="example"></a>Exemple

```cpp
// istreambuf_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;
      ++inpos;   //Increment istreambuf_iterator
      ++outpos;
   }
}
```

## <a name="istreambuf_iteratoroperator-gt"></a><a name="op_arrow"></a> istreambuf_iterator :: Operator-&gt;

Retourne la valeur d'un membre, le cas échéant.

```cpp
const Elem* operator->() const;
```

### <a name="return-value"></a>Valeur renvoyée

L’opérateur retourne **& \* \* This**.

## <a name="istreambuf_iteratorstreambuf_type"></a><a name="streambuf_type"></a> istreambuf_iterator :: streambuf_type

Type qui fournit le type de flux de istreambuf_iterator.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `basic_streambuf` \< **CharType**, **Traits**> .

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `istreambuf_type`, consultez l’exemple relatif à [istreambuf_iterator](#istreambuf_iterator).

## <a name="istreambuf_iteratortraits_type"></a><a name="traits_type"></a> istreambuf_iterator :: traits_type

Type qui fournit le type de caractéristique de `istream_iterator`.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle *Traits*.

### <a name="example"></a>Exemple

```cpp
// istreambuf_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="see-also"></a>Voir aussi

[Iterator, struct](../standard-library/iterator-struct.md)\
[\<iterator>](../standard-library/iterator.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
