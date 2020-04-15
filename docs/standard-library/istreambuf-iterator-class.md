---
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
ms.openlocfilehash: 80bca2160f2e60938e9d0c85557b11a273c23264
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363063"
---
# <a name="istreambuf_iterator-class"></a>istreambuf_iterator, classe

Le modèle de classe istreambuf_iterator décrit un objet itérateur d’entrée qui extrait des éléments de caractère à partir `basic_streambuf` \< d’un tampon de flux d’entrée, auquel il accède par un objet qu’il stocke, de pointeur de type à **CharType**, **Traits**>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType class Traits = char_traits <CharType>>
class istreambuf_iterator
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```

### <a name="parameters"></a>Paramètres

*CharType CharType*\
Type qui représente le type de caractère pour istreambuf_iterator.

*Traits*\
Type qui représente le type de caractère pour istreambuf_iterator. Cet argument est facultatif et sa valeur par défaut est `char_traits`\< *CharType>.*

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
|[Égal](#equal)|Vérifie l'égalité de deux itérateurs de tampon de flux d'entrée.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur](#op_star)|L'opérateur de suppression de référence retourne le caractère suivant du flux.|
|[opérateur](#op_add_add)|Retourne le caractère suivant du flux d'entrée ou copie l'objet avant de l'incrémenter et de retourner sa copie.|
|[>opérateur](#op_arrow)|Retourne la valeur d'un membre, le cas échéant.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<iterator>

**Espace de noms :** std

## <a name="istreambuf_iteratorchar_type"></a><a name="char_type"></a>istreambuf_iterator::char_type

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

## <a name="istreambuf_iteratorequal"></a><a name="equal"></a>istreambuf_iterator::égal

Teste l’équivalence de deux itérateurs de mémoire tampon de flux d’entrée.

```cpp
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
Itérateur pour lequel vérifier l’égalité.

### <a name="return-value"></a>Valeur de retour

**true** si les deux `istreambuf_iterator`s sont des itérateurs de fin de flux ou si aucun des deux n’est un itérateur de fin du flux. Sinon, **false**.

### <a name="remarks"></a>Notes

Une plage est `istreambuf_iterator` définie par la position actuelle et l’itérateur de fin de flux, mais puisque `equal` tous les itérateurs de flux non-fin de flux sont équivalents sous la fonction membre, il n’est pas possible de définir les sous-arrangements à l’aide `istreambuf_iterator`de s. Les opérateurs `==` et `!=` ont la même sémantique.

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

## <a name="istreambuf_iteratorint_type"></a><a name="int_type"></a>istreambuf_iterator::int_type

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

## <a name="istreambuf_iteratoristream_type"></a><a name="istream_type"></a>istreambuf_iterator::istream_type

Type qui fournit le type de flux de `istreambuf_iterator`.

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Notes

Le type est synonyme `basic_istream` \< de **CharType**, **Traits**>.

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `istream_type`, consultez l’exemple relatif à [istreambuf_iterator](#istreambuf_iterator).

## <a name="istreambuf_iteratoristreambuf_iterator"></a><a name="istreambuf_iterator"></a>istreambuf_iterator::istreambuf_iterator

Construit un istreambuf_iterator qui est initialisé pour lire des caractères à partir du flux d’entrée.

```cpp
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```

### <a name="parameters"></a>Paramètres

*strbuf (strbuf)*\
Mémoire tampon de flux d’entrée à laquelle le `istreambuf_iterator` est attaché.

*_Istr*\
Flux d’entrée auquel le `istreambuf_iterator` est attaché.

### <a name="remarks"></a>Notes

Le premier constructeur initialise le pointeur tampon de flux d’entrée avec *strbuf.* Le deuxième constructeur initialise le pointeur tampon du flux d’entrée avec *_Istr*. `rdbuf`, puis tente finalement d’extraire `CharType`et de stocker un objet de type .

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

## <a name="istreambuf_iteratoroperator"></a><a name="op_star"></a>istreambuf_iterator::opérateur

L'opérateur de suppression de référence retourne le caractère suivant du flux.

```cpp
CharType operator*() const;
```

### <a name="return-value"></a>Valeur de retour

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

## <a name="istreambuf_iteratoroperator"></a><a name="op_add_add"></a>istreambuf_iterator ::opérateur

Retourne le caractère suivant du flux d'entrée ou copie l'objet avant de l'incrémenter et de retourner sa copie.

```cpp
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Valeur de retour

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

## <a name="istreambuf_iteratoroperator-gt"></a><a name="op_arrow"></a>istreambuf_iterator::opérateur-&gt;

Retourne la valeur d'un membre, le cas échéant.

```cpp
const Elem* operator->() const;
```

### <a name="return-value"></a>Valeur de retour

L’opérateur ** & \* \*** retourne ceci .

## <a name="istreambuf_iteratorstreambuf_type"></a><a name="streambuf_type"></a>istreambuf_iterator::streambuf_type

Type qui fournit le type de flux de istreambuf_iterator.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Notes

Le type est synonyme `basic_streambuf` \< de **CharType**, **Traits**>.

### <a name="example"></a>Exemple

Pour découvrir comment déclarer et utiliser `istreambuf_type`, consultez l’exemple relatif à [istreambuf_iterator](#istreambuf_iterator).

## <a name="istreambuf_iteratortraits_type"></a><a name="traits_type"></a>istreambuf_iterator::traits_type

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

[struct d’itérateur](../standard-library/iterator-struct.md)\
[\<itérateur>](../standard-library/iterator.md)\
[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Référence de bibliothèque standard de CMD](../standard-library/cpp-standard-library-reference.md)
