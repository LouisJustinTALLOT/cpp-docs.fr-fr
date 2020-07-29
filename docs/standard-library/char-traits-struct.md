---
title: char_traits, struct
ms.date: 05/07/2019
f1_keywords:
- iosfwd/std::char_traits
- iosfwd/std::char_traits::char_type
- iosfwd/std::char_traits::int_type
- iosfwd/std::char_traits::off_type
- iosfwd/std::char_traits::pos_type
- iosfwd/std::char_traits::state_type
- iosfwd/std::char_traits::assign
- iosfwd/std::char_traits::compare
- iosfwd/std::char_traits::copy
- iosfwd/std::char_traits::_Copy_s
- iosfwd/std::char_traits::eof
- iosfwd/std::char_traits::eq
- iosfwd/std::char_traits::eq_int_type
- iosfwd/std::char_traits::find
- iosfwd/std::char_traits::length
- iosfwd/std::char_traits::lt
- iosfwd/std::char_traits::move
- iosfwd/std::char_traits::_Move_s
- iosfwd/std::char_traits::not_eof
- iosfwd/std::char_traits::to_char_type
- iosfwd/std::char_traits::to_int_type
helpviewer_keywords:
- char_traits struct
- char_traits class
ms.assetid: 568e59f0-4521-4207-9223-9dcf6a16d620
ms.openlocfilehash: 834572e96d9d8c19ae5d75a57dfa6c0053ae0ec5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222600"
---
# <a name="char_traits-struct"></a>char_traits, struct

La structure char_traits décrit les attributs associés à un caractère.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
struct char_traits;
```

### <a name="parameters"></a>Paramètres

*CharType*\
Type de données de l'élément.

## <a name="remarks"></a>Notes

Le struct de modèle décrit différentes caractéristiques de caractères pour le type `CharType` . Le modèle de classe [basic_string](../standard-library/basic-string-class.md) ainsi que plusieurs modèles de classe iostream, y compris [basic_ios](../standard-library/basic-ios-class.md), utilisent ces informations pour manipuler les éléments de type `CharType` . Un tel type d'élément ne doit pas requérir une construction ou une destruction explicite. Il doit fournir un constructeur par défaut, un constructeur de copie et un opérateur d'affectation avec la sémantique attendue. Une copie au niveau du bit doit avoir le même effet qu'une affectation. Aucune des fonctions membres de la structure char_traits ne peut lever des exceptions.

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type de caractère.|
|[int_type](#int_type)|Type entier qui peut représenter un caractère de type `char_type` ou un caractère de fin de fichier (EOF).|
|[off_type](#off_type)|Type entier qui peut représenter des décalages entre les positions dans un flux.|
|[pos_type](#pos_type)|Type entier qui peut représenter des positions dans un flux.|
|[state_type](#state_type)|Type qui représente l'état de la conversion de caractères multi-octets dans un flux.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[assign](#assign)|Affecte la valeur d'un caractère à un autre.|
|[compar](#compare)|Compare un nombre spécifié de caractères dans deux chaînes.|
|[copy](#copy)|Copie un nombre spécifié de caractères d'une chaîne vers une autre. Obsolète. Utilisez [char_traits::_Copy_s](#copy_s) à la place.|
|[_Copy_s](#copy_s)|Copie un nombre spécifié de caractères d'une chaîne vers une autre.|
|[EOF](#eof)|Retourne le caractère de fin de fichier (EOF).|
|[eq](#eq)|Teste si deux caractères `char_type` sont égaux.|
|[eq_int_type](#eq_int_type)|Teste si deux caractères représentés comme `int_type` sont égaux.|
|[find](#find)|Recherche la première occurrence d'un caractère spécifié dans une plage de caractères.|
|[length](#length)|Retourne la longueur d'une chaîne.|
|[lt](#lt)|Teste si un caractère est inférieur à un autre.|
|[move](#move)|Copie un nombre spécifié de caractères d'une séquence vers une autre séquence qui la chevauche éventuellement. Obsolète. Utilisez [char_traits::_Move_s](#move_s) à la place.|
|[_Move_s](#move_s)|Copie un nombre spécifié de caractères d'une séquence vers une autre séquence qui la chevauche éventuellement.|
|[not_eof](#not_eof)|Teste si un caractère est le caractère de fin de fichier (EOF).|
|[to_char_type](#to_char_type)|Convertit un caractère `int_type` en caractère `char_type` correspondant et retourne le résultat.|
|[to_int_type](#to_int_type)|Convertit un caractère `char_type` en caractère `int_type` correspondant et retourne le résultat.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<string>

**Espace de noms :** std

## <a name="char_traitsassign"></a><a name="assign"></a>char_traits :: assign

Assigne la valeur d’un caractère à un autre ou à une plage d’éléments dans une chaîne.

```cpp
static void assign(char_type& _CharTo,
    const char_type& _CharFrom);

static char_type *assign(char_type* strTo,
    size_t _Num,
    char_type _CharFrom);
```

### <a name="parameters"></a>Paramètres

**_** *CharFrom* le caractère dont la valeur doit être affectée.

*_CharTo*\
Élément qui doit être auquel doit être affectée la valeur du caractère.

*strTo*\
Tableau de chaînes ou de caractères dont les éléments initiaux doivent recevoir des valeurs de caractère.

*_Num*\
Nombre d’éléments auxquels des valeurs vont être assignées.

### <a name="return-value"></a>Valeur de retour

La deuxième fonction membre retourne un pointeur vers la chaîne dont les premières *_Num* éléments ont été affectées à des valeurs de *_CharFrom*.

### <a name="example"></a>Exemple

```cpp
// char_traits_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning
   // one character value to another character
   char ChTo = 't';
   const char ChFrom = 'f';
   cout << "The initial characters ( ChTo , ChFrom ) are: ( "
        << ChTo << " , " << ChFrom << " )." << endl;
   char_traits<char>::assign ( ChTo , ChFrom );
   cout << "After assigning, the characters ( ChTo , ChFrom ) are: ( "
        << ChTo << " , " << ChFrom << " )." << endl << endl;

   // The second member function assigning
   // character values to initial part of a string
   char_traits<char>::char_type s1[] = "abcd-1234-abcd";
   char_traits<char>::char_type* result1;
   cout << "The target string s1 is: " << s1 << endl;
   result1 = char_traits<char>::assign ( s1 , 4 , 'f' );
   cout << "The result1 = assign ( s1 , 4 , 'f' ) is: "
        << result1 << endl;
}
```

```Output
The initial characters ( ChTo , ChFrom ) are: ( t , f ).
After assigning, the characters ( ChTo , ChFrom ) are: ( f , f ).

The target string s1 is: abcd-1234-abcd
The result1 = assign ( s1 , 4 , 'f' ) is: ffff-1234-abcd
```

## <a name="char_traitschar_type"></a><a name="char_type"></a>char_traits :: char_type

Type de caractère.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `CharType`.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [copy](#copy) pour savoir comment déclarer et utiliser `char_type`.

## <a name="char_traitscompare"></a><a name="compare"></a>char_traits :: compare

Compare un nombre spécifié de caractères dans deux chaînes.

```cpp
static int compare(const char_type* str1,
    const char_type* str2,
    size_t _Num);
```

### <a name="parameters"></a>Paramètres

*str1*\
Première de deux chaînes à comparer à l’autre.

*répartition*\
Deuxième de deux chaînes à comparer à l’autre.

*_Num*\
Nombre d’éléments dans les chaînes à comparer.

### <a name="return-value"></a>Valeur de retour

Une valeur négative si la première chaîne est inférieure à la deuxième ; 0 si les deux chaînes sont égales ; ou une valeur positive si la première chaîne est supérieure à la deuxième.

### <a name="remarks"></a>Notes

La comparaison entre les chaînes est effectuée élément par élément, en commençant par vérifier leur égalité, puis, si une paire d’éléments dans la séquence n’est pas identique, les deux éléments sont comparés pour vérifier si l’un est inférieur à l’autre.

Si deux chaînes sont égales sur une plage, mais que l’une est plus longue que l’autre, la plus courte des deux est inférieure à la plus longue.

### <a name="example"></a>Exemple

```cpp
// char_traits_compare.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main() {
   using namespace std;

   char_traits<char>::char_type* s1 = "CAB";
   char_traits<char>::char_type* s2 = "ABC";
   char_traits<char>::char_type* s3 = "ABC";
   char_traits<char>::char_type* s4 = "ABCD";

   cout << "The string s1 is: " << s1 << endl;
   cout << "The string s2 is: " << s2 << endl;
   cout << "The string s3 is: " << s3 << endl;
   cout << "The string s4 is: " << s4 << endl;

   int comp1, comp2, comp3, comp4;
   comp1 = char_traits<char>::compare ( s1 , s2 , 2 );
   comp2 = char_traits<char>::compare ( s2 , s3 , 3 );
   comp3 = char_traits<char>::compare ( s3 , s4 , 4 );
   comp4 = char_traits<char>::compare ( s4 , s3 , 4 );
   cout << "compare ( s1 , s2 , 2 ) = " << comp1 << endl;
   cout << "compare ( s2 , s3 , 3 ) = " << comp2 << endl;
   cout << "compare ( s3 , s4 , 4 ) = " << comp3 << endl;
   cout << "compare ( s4 , s3 , 4 ) = " << comp4 << endl;
}
```

## <a name="char_traitscopy"></a><a name="copy"></a>char_traits :: copier

Copie un nombre spécifié de caractères d'une chaîne vers une autre.

Cette méthode est potentiellement dangereuse, car elle suppose que l’appelant vérifie que les valeurs passées sont correctes. Utilisez [char_traits::_Copy_s](#copy_s) à la place.

```cpp
static char_type *copy(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>Paramètres

*_To*\
Élément au début du tableau de chaînes ou de caractères ciblé pour recevoir la séquence de caractères copiée.

*_From*\
Élément au début du tableau source de chaînes ou de caractères à copier.

*_Num*\
Nombre d’éléments à copier.

### <a name="return-value"></a>Valeur de retour

Premier élément copié dans le tableau de chaînes ou de caractères ciblé pour recevoir la séquence de caractères copiée.

### <a name="remarks"></a>Notes

Les séquences de caractères source et de destination ne doivent pas se chevaucher.

### <a name="example"></a>Exemple

```cpp
// char_traits_copy.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type s1[] = "abcd-1234-abcd";
   char_traits<char>::char_type s2[] = "ABCD-1234";
   char_traits<char>::char_type* result1;
   cout << "The source string is: " << s1 << endl;
   cout << "The destination string is: " << s2 << endl;
   // Note: char_traits::copy is potentially unsafe, consider
   // using char_traits::_Copy_s instead.
   result1 = char_traits<char>::copy ( s1 , s2 , 4 );  // C4996
   cout << "The result1 = copy ( s1 , s2 , 4 ) is: "
        << result1 << endl;
}
```

```Output
The source string is: abcd-1234-abcd
The destination string is: ABCD-1234
The result1 = copy ( s1 , s2 , 4 ) is: ABCD-1234-abcd
```

## <a name="char_traits_copy_s"></a><a name="copy_s"></a>char_traits :: _Copy_s

Copie un nombre spécifié de caractères d'une chaîne vers une autre.

```cpp
static char_type *_Copy_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>Paramètres

*dest*\
Tableau de chaînes ou de caractères ciblé pour recevoir la séquence de caractères copiée.

*dest_size*\
La taille de *dest*. Si `char_type` est **`char`** , cette taille est en octets. Si `char_type` est **`wchar_t`** , cette taille est en mots.

*_From*\
Tableau source de chaînes ou de caractères à copier.

*saut*\
Nombre d’éléments à copier.

### <a name="return-value"></a>Valeur de retour

Tableau de chaînes ou de caractères ciblé pour recevoir la séquence de caractères copiée.

### <a name="remarks"></a>Notes

Les séquences de caractères source et de destination ne doivent pas se chevaucher.

### <a name="example"></a>Exemple

```cpp
// char_traits__Copy_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;

    char_traits<char>::char_type s1[] = "abcd-1234-abcd";
    char_traits<char>::char_type s2[] = "ABCD-1234";
    char_traits<char>::char_type* result1;
    cout << "The source string is: " << s1 << endl;
    cout << "The destination string is: " << s2 << endl;
    result1 = char_traits<char>::_Copy_s(s1,
        char_traits<char>::length(s1), s2, 4);
    cout << "The result1 = _Copy_s(s1, "
         << "char_traits<char>::length(s1), s2, 4) is: "
         << result1 << endl;
}
```

```Output
The source string is: abcd-1234-abcd
The destination string is: ABCD-1234
The result1 = _Copy_s(s1, char_traits<char>::length(s1), s2, 4) is: ABCD-1234-abcd
```

## <a name="char_traitseof"></a><a name="eof"></a>char_traits :: EOF

Retourne le caractère de fin de fichier (EOF).

```cpp
static int_type eof();
```

### <a name="return-value"></a>Valeur de retour

Caractère EOF.

### <a name="remarks"></a>Notes

Valeur qui représente la fin du fichier (par exemple, EOF ou WEOF).

La norme C++ stipule que cette valeur ne doit pas correspondre à une valeur `char_type` valide. Le compilateur Microsoft C++ applique cette contrainte pour le type **`char`** , mais pas pour le type **`wchar_t`** . C'est ce qu'illustre l'exemple ci-dessous.

### <a name="example"></a>Exemple

```cpp
// char_traits_eof.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main()
{
    using namespace std;

    char_traits<char>::char_type ch1 = 'x';
    char_traits<char>::int_type int1;
    int1 = char_traits<char>::to_int_type(ch1);
    cout << "char_type ch1 is '" << ch1 << "' and corresponds to int_type "
         << int1 << "." << endl << endl;

    char_traits<char>::int_type int2 = char_traits<char>::eof();
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;

    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;
}
```

```Output
char_type ch1 is 'x' and corresponds to int_type 120.

The eof marker for char_traits<char> is: -1
The eof marker for char_traits<wchar_t> is: 65535
```

## <a name="char_traitseq"></a><a name="eq"></a>char_traits :: EQ

Teste si deux caractères `char_type` sont égaux.

```cpp
static bool eq(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>Paramètres

*_Ch1*\
Premier de deux caractères dont l’égalité est à vérifier.

*_Ch2*\
Deuxième de deux caractères dont l’égalité est à vérifier.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le premier caractère est égal au deuxième caractère ; Sinon, **`false`** .

### <a name="example"></a>Exemple

```cpp
// char_traits_eq.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'x';

   // Testing for equality
   bool b1 = char_traits<char>::eq ( ch1 , ch2 );
   if ( b1 )
      cout << "The character ch1 is equal "
           << "to the character ch2." << endl;
   else
      cout << "The character ch1 is not equal "
           << "to the character ch2." << endl;

   // An equivalent and alternatively test procedure
   if ( ch1 == ch3 )
      cout << "The character ch1 is equal "
           << "to the character ch3." << endl;
   else
      cout << "The character ch1 is not equal "
           << "to the character ch3." << endl;
}
```

```Output
The character ch1 is not equal to the character ch2.
The character ch1 is equal to the character ch3.
```

## <a name="char_traitseq_int_type"></a><a name="eq_int_type"></a>char_traits :: eq_int_type

Vérifie si deux caractères représentés sous la forme d’un `int_type` sont égaux ou non.

```cpp
static bool eq_int_type(const int_type& _Ch1, const int_type& _Ch2);
```

### <a name="parameters"></a>Paramètres

*_Ch1*\
Premier des deux caractères dont l’égalité doit être testée en tant que `int_type` s.

*_Ch2*\
Deuxième de deux caractères dont l’égalité est à vérifier, représentés sous la forme d’un `int_type`s.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le premier caractère est égal au deuxième caractère ; Sinon, **`false`** .

### <a name="example"></a>Exemple

```cpp
// char_traits_eq_int_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'x';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Testing for equality of int_type representations
   bool b1 = char_traits<char>::eq_int_type ( int1 , int2 );
   if ( b1 )
      cout << "The int_type representation of character ch1\n "
           << "is equal to the int_type representation of ch2."
           << endl;
   else
      cout << "The int_type representation of character ch1\n is "
           << "not equal to the int_type representation of ch2."
           << endl;

   // An equivalent and alternatively test procedure
   if ( int1 == int3 )
      cout << "The int_type representation of character ch1\n "
           << "is equal to the int_type representation of ch3."
           << endl;
   else
      cout << "The int_type representation of character ch1\n is "
           << "not equal to the int_type representation of ch3."
           << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = x corresponding to int1 = 120.
    ch2 = y corresponding to int1 = 121.
    ch3 = x corresponding to int1 = 120.

The int_type representation of character ch1
is not equal to the int_type representation of ch2.
The int_type representation of character ch1
is equal to the int_type representation of ch3.
```

## <a name="char_traitsfind"></a><a name="find"></a>char_traits :: find

Recherche la première occurrence d'un caractère spécifié dans une plage de caractères.

```cpp
static const char_type* find(const char_type* str,
    size_t _Num,
    const char_type& _Ch);
```

### <a name="parameters"></a>Paramètres

*Str*\
Premier caractère de la chaîne dans laquelle s’effectue la recherche.

*_Num*\
Nombre de positions, à partir de la première, de la plage dans laquelle s’effectue la recherche.

*_Ch*\
Caractère à rechercher dans la plage.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la première occurrence du caractère spécifié dans la plage si une correspondance est trouvée ; sinon, un pointeur null.

### <a name="example"></a>Exemple

```cpp
// char_traits_find.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   const char* s1 = "f2d-1234-abcd";
   const char* result1;
   cout << "The string to be searched is: " << s1 << endl;

   // Searching for a 'd' in the first 6 positions of string s1
   result1 = char_traits<char>::find ( s1 , 6 , 'd');
   cout << "The character searched for in s1 is: "
        << *result1 << endl;
   cout << "The string beginning with the first occurrence\n "
        << "of the character 'd' is: " << result1 << endl;

   // When no match is found the NULL value is returned
   const char* result2;
   result2 = char_traits<char>::find ( s1 , 3 , 'a');
   if ( result2 == NULL )
      cout << "The result2 of the search is NULL." << endl;
   else
      cout << "The result2 of the search  is: " << result1
           << endl;
}
```

```Output
The string to be searched is: f2d-1234-abcd
The character searched for in s1 is: d
The string beginning with the first occurrence
of the character 'd' is: d-1234-abcd
The result2 of the search is NULL.
```

## <a name="char_traitsint_type"></a><a name="int_type"></a>char_traits :: int_type

Type entier qui peut représenter un caractère de type `char_type` ou un caractère de fin de fichier (EOF).

```cpp
typedef long int_type;
```

### <a name="remarks"></a>Notes

Il doit être possible de taper un cast d’une valeur de type `CharType` pour `int_type` revenir à `CharType` sans modifier la valeur d’origine.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [eq_int_type](#eq_int_type) pour savoir comment déclarer et utiliser `int_type`.

## <a name="char_traitslength"></a><a name="length"></a>char_traits :: length

Retourne la longueur d'une chaîne.

```cpp
static size_t length(const char_type* str);
```

### <a name="parameters"></a>Paramètres

*Str*\
Chaîne C dont la longueur doit être mesurée.

### <a name="return-value"></a>Valeur de retour

Nombre d’éléments dans la séquence mesurée, sans inclure le terminateur null.

### <a name="example"></a>Exemple

```cpp
// char_traits_length.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   const char* str1= "Hello";
   cout << "The C-string str1 is: " << str1 << endl;

   size_t lenStr1;
   lenStr1 = char_traits<char>::length ( str1 );
   cout << "The length of C-string str1 is: "
        << lenStr1 << "." << endl;
}
```

```Output
The C-string str1 is: Hello
The length of C-string str1 is: 5.
```

## <a name="char_traitslt"></a><a name="lt"></a>char_traits :: lt

Teste si un caractère est inférieur à un autre.

```cpp
static bool lt(const char_type& _Ch1, const char_type& _Ch2);
```

### <a name="parameters"></a>Paramètres

*_Ch1*\
Premier de deux caractères dont la relation Inférieur à est à vérifier.

*_Ch2*\
Deuxième de deux caractères dont la relation Inférieur à est à vérifier.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le premier caractère est inférieur au deuxième caractère ; Sinon, **`false`** .

### <a name="example"></a>Exemple

```cpp
// char_traits_lt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::char_type ch2 =  'y';
   char_traits<char>::char_type ch3 =  'z';

   // Testing for less than
   bool b1 = char_traits<char>::lt ( ch1 , ch2 );
   if ( b1 )
      cout << "The character ch1 is less than "
           << "the character ch2." << endl;
   else
      cout << "The character ch1 is not less "
           << "than the character ch2." << endl;

   // An equivalent and alternatively test procedure
   if ( ch3 <  ch2 )
      cout << "The character ch3 is less than "
           << "the character ch2." << endl;
   else
      cout << "The character ch3 is not less "
           << "than the character ch2." << endl;
}
```

```Output
The character ch1 is less than the character ch2.
The character ch3 is not less than the character ch2.
```

## <a name="char_traitsmove"></a><a name="move"></a>char_traits :: Move

Copie un nombre spécifié de caractères d’une séquence dans une autre qui la chevauche éventuellement.

Cette méthode est potentiellement dangereuse, car elle suppose que l’appelant vérifie que les valeurs passées sont correctes. Utilisez [char_traits::_Move_s](#move_s) à la place.

```cpp
static char_type *move(char_type* _To,
    const char_type* _From,
    size_t _Num);
```

### <a name="parameters"></a>Paramètres

*_To*\
Élément au début du tableau de chaînes ou de caractères ciblé pour recevoir la séquence de caractères copiée.

*_From*\
Élément au début du tableau source de chaînes ou de caractères à copier.

*_Num*\
Nombre d’éléments à copier à partir de la chaîne source.

### <a name="return-value"></a>Valeur de retour

Le premier élément *_To* copié dans le tableau de chaînes ou de caractères ciblé pour recevoir la séquence de caractères copiée.

### <a name="remarks"></a>Notes

La source et la destination peuvent se chevaucher.

### <a name="example"></a>Exemple

```cpp
// char_traits_move.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";
   char_traits<char>::char_type sTo1[] =  "ABCD-1234";
   char_traits<char>::char_type* result1;
   cout << "The source string sFrom1 is: " << sFrom1 << endl;
   cout << "The destination stringsTo1 is: " << sTo1 << endl;
   // Note: char_traits::move is potentially unsafe, consider
   // using char_traits::_Move_s instead.
   result1 = char_traits<char>::move ( sTo1 ,  sFrom1 , 4 );  // C4996
   cout << "The result1 = move ( sTo1 , sFrom1 , 4 ) is: "
        << result1 << endl << endl;

   // When source and destination overlap
   char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";
   char_traits<char>::char_type* result2;
   cout << "The source/destination string sToFrom2 is: "
        << sToFrom2 << endl;
   const char* findc = char_traits<char>::find ( sToFrom2 , 4 , 'c' );
   // Note: char_traits::move is potentially unsafe, consider
   // using char_traits::_Move_s instead.
   result2 = char_traits<char>::move ( sToFrom2 , findc , 8 );  // C4996
   cout << "The result2 = move ( sToFrom2 , findc , 8 ) is: "
        << result2 << endl;
}
```

```Output
The source string sFrom1 is: abcd-1234-abcd
The destination stringsTo1 is: ABCD-1234
The result1 = move ( sTo1 , sFrom1 , 4 ) is: abcd-1234

The source/destination string sToFrom2 is: abcd-1234-ABCD
The result2 = move ( sToFrom2 , findc , 8 ) is: cd-1234-4-ABCD
```

## <a name="char_traits_move_s"></a><a name="move_s"></a>char_traits :: _Move_s

Copie un nombre spécifié de caractères d’une séquence dans une autre qui la chevauche éventuellement.

```cpp
static char_type *_Move_s(
    char_type* dest,
    size_t dest_size,
    const char_type* _From,
    size_t count);
```

### <a name="parameters"></a>Paramètres

*dest*\
Élément au début du tableau de chaînes ou de caractères ciblé pour recevoir la séquence de caractères copiée.

*dest_size*\
La taille de *dest*. Si `char_type` est **`char`** , il est en octets. Si `char_type` est **`wchar_t`** , il s’agit de mots.

*_From*\
Élément au début du tableau source de chaînes ou de caractères à copier.

*saut*\
Nombre d’éléments à copier à partir de la chaîne source.

### <a name="return-value"></a>Valeur de retour

Le premier élément *dest* copié dans le tableau de chaînes ou de caractères ciblé pour recevoir la séquence de caractères copiée.

### <a name="remarks"></a>Notes

La source et la destination peuvent se chevaucher.

### <a name="example"></a>Exemple

```cpp
// char_traits__Move_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;

    char_traits<char>::char_type sFrom1[] =  "abcd-1234-abcd";
    char_traits<char>::char_type sTo1[] =  "ABCD-1234";
    char_traits<char>::char_type* result1;
    cout << "The source string sFrom1 is: " << sFrom1 << endl;
    cout << "The destination stringsTo1 is: " << sTo1 << endl;
    result1 = char_traits<char>::_Move_s(sTo1,
        char_traits<char>::length(sTo1), sFrom1, 4);
    cout << "The result1 = _Move_s(sTo1, "
         << "char_traits<char>::length(sTo1), sFrom1, 4) is: "
         << result1 << endl << endl;

    // When source and destination overlap
    char_traits<char>::char_type sToFrom2[] = "abcd-1234-ABCD";
    char_traits<char>::char_type* result2;
    cout << "The source/destination string sToFrom2 is: "
         << sToFrom2 << endl;
    const char* findc = char_traits<char>::find(sToFrom2, 4, 'c');
    result2 = char_traits<char>::_Move_s(sToFrom2,
        char_traits<char>::length(sToFrom2), findc, 8);
    cout << "The result2 = _Move_s(sToFrom2, "
        << "char_traits<char>::length(sToFrom2), findc, 8) is: "
         << result2 << endl;
}
```

```Output
The source string sFrom1 is: abcd-1234-abcd
The destination stringsTo1 is: ABCD-1234
The result1 = _Move_s(sTo1, char_traits<char>::length(sTo1), sFrom1, 4) is: abcd-1234

The source/destination string sToFrom2 is: abcd-1234-ABCD
The result2 = _Move_s(sToFrom2, char_traits<char>::length(sToFrom2), findc, 8) is: cd-1234-4-ABCD
```

## <a name="char_traitsnot_eof"></a><a name="not_eof"></a>char_traits :: not_eof

Vérifie si un caractère est ou n’est pas le caractère de fin de fichier (EOF).

```cpp
static int_type not_eof(const int_type& _Ch);
```

### <a name="parameters"></a>Paramètres

*_Ch*\
Caractère représenté sous la forme d’un `int_type` à vérifier pour déterminer s’il est ou non le caractère EOF.

### <a name="return-value"></a>Valeur de retour

`int_type`Représentation du caractère testé, si le `int_type` du caractère n’est pas égal à celui du caractère EOF.

Si la `int_type` valeur de caractère est égale à la `int_type` valeur EOF, alors **`false`** .

### <a name="example"></a>Exemple

```cpp
// char_traits_not_eof.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( ) {
   using namespace std;

   char_traits<char>::char_type ch1 =  'x';
   char_traits<char>::int_type int1;
   int1 = char_traits<char>:: to_int_type ( ch1 );
   cout << "The char_type ch1 is " << ch1
        << " corresponding to int_type: "
        << int1 << "." << endl;

   // EOF member function
   char_traits <char>::int_type int2 = char_traits<char>::eof ( );
   cout << "The eofReturn is: " << int2 << endl;

   // Testing for EOF or another character
   char_traits <char>::int_type eofTest1, eofTest2;
   eofTest1 = char_traits<char>::not_eof ( int1 );
   if ( !eofTest1 )
      cout << "The eofTest1 indicates ch1 is an EOF character."
              << endl;
   else
      cout << "The eofTest1 returns: " << eofTest1
           << ", which is the character: "
           <<  char_traits<char>::to_char_type ( eofTest1 )
           << "." << endl;

   eofTest2 = char_traits<char>::not_eof ( int2 );
   if ( !eofTest2 )
      cout << "The eofTest2 indicates int2 is an EOF character."
           << endl;
   else
      cout << "The eofTest1 returns: " << eofTest2
           << ", which is the character: "
           <<  char_traits<char>::to_char_type ( eofTest2 )
           << "." << endl;
}
```

```Output
The char_type ch1 is x corresponding to int_type: 120.
The eofReturn is: -1
The eofTest1 returns: 120, which is the character: x.
The eofTest2 indicates int2 is an EOF character.
```

## <a name="char_traitsoff_type"></a><a name="off_type"></a>char_traits :: off_type

Type entier qui peut représenter des décalages entre les positions dans un flux.

```cpp
typedef streamoff off_type;
```

### <a name="remarks"></a>Notes

Le type est un entier signé qui décrit un objet capable de stocker un décalage d’octet impliqué dans différentes opérations de positionnement de flux. Il s’agit généralement d’un synonyme de [streamoff](../standard-library/ios-typedefs.md#streamoff), mais il a essentiellement les mêmes propriétés que ce type.

## <a name="char_traitspos_type"></a><a name="pos_type"></a>char_traits ::p os_type

Type entier qui peut représenter des positions dans un flux.

```cpp
typedef streampos pos_type;
```

### <a name="remarks"></a>Notes

Le type décrit un objet capable de stocker toutes les informations nécessaires à la restauration d’un indicateur de position de fichier arbitraire dans un flux. Il s’agit généralement d’un synonyme de [streampos](../standard-library/ios-typedefs.md#streampos), mais dans tous les cas, il a essentiellement les mêmes propriétés que ce type.

## <a name="char_traitsstate_type"></a><a name="state_type"></a>char_traits :: state_type

Type qui représente l’état de la conversion de caractères multioctets dans un flux.

```cpp
typedef implementation-defined state_type;
```

### <a name="remarks"></a>Notes

Le type décrit un objet qui peut représenter un état de conversion. Il s’agit généralement d’un synonyme de `mbstate_t`, mais dans tous les cas, il a essentiellement les mêmes propriétés que ce type.

## <a name="char_traitsto_char_type"></a><a name="to_char_type"></a>char_traits :: to_char_type

Convertit un caractère `int_type` en caractère `char_type` correspondant et retourne le résultat.

```cpp
static char_type to_char_type(const int_type& _Ch);
```

### <a name="parameters"></a>Paramètres

*_Ch*\
Caractère `int_type` à représenter sous la forme d’un `char_type`.

### <a name="return-value"></a>Valeur de retour

Caractère `char_type` correspondant au caractère `int_type`.

Une valeur de *_Ch* qui ne peut pas être représentée en tant que génère un résultat non spécifié.

### <a name="remarks"></a>Notes

Les opérations de conversion [to_int_type](#to_int_type) et `to_char_type` sont l’inverse l’une de l’autre, de sorte que :

`to_int_type` ( `to_char_type` ( *x* ) ) == *x*

pour tout `int_type` *x* et

`to_char_type` ( `to_int_type` ( *x* ) ) == *x*

pour tout `char_type` *x*.

### <a name="example"></a>Exemple

```cpp
// char_traits_to_char_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   char_traits<char>::char_type ch1 =  'a';
   char_traits<char>::char_type ch2 =  'b';
   char_traits<char>::char_type ch3 =  'a';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Converting from int_type back to char_type
   char_traits<char>::char_type rec_ch1;
   rec_ch1 = char_traits<char>:: to_char_type ( int1);
   char_traits<char>::char_type rec_ch2;
   rec_ch2 = char_traits<char>:: to_char_type ( int2);

   cout << "The recovered char_types and corresponding int_types are:"
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "
        << int1 << "."
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "
        << int2 << "." << endl << endl;

   // Testing that the conversions are inverse operations
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );
   if ( b1 )
      cout << "The recovered char_type of ch1"
           << " is equal to the original ch1." << endl;
   else
      cout << "The recovered char_type of ch1"
           << " is not equal to the original ch1." << endl;

   // An equivalent and alternatively test procedure
   if ( rec_ch2 == ch2 )
      cout << "The recovered char_type of ch2"
           << " is equal to the original ch2." << endl;
   else
      cout << "The recovered char_type of ch2"
           << " is not equal to the original ch2." << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = a corresponding to int1 = 97.
    ch2 = b corresponding to int1 = 98.
    ch3 = a corresponding to int1 = 97.

The recovered char_types and corresponding int_types are:
    recovered ch1 = a from int1 = 97.
    recovered ch2 = b from int2 = 98.

The recovered char_type of ch1 is equal to the original ch1.
The recovered char_type of ch2 is equal to the original ch2.
```

## <a name="char_traitsto_int_type"></a><a name="to_int_type"></a>char_traits :: to_int_type

Convertit un caractère `char_type` en caractère `int_type` correspondant et retourne le résultat.

```cpp
static int_type to_int_type(const char_type& _Ch);
```

### <a name="parameters"></a>Paramètres

*_Ch*\
Caractère `char_type` à représenter sous la forme d’un `int_type`.

### <a name="return-value"></a>Valeur de retour

Caractère `int_type` correspondant au caractère `char_type`.

### <a name="remarks"></a>Notes

Les opérations de conversion `to_int_type` et [to_char_type](#to_char_type) sont l’inverse l’une de l’autre, de sorte que :

`to_int_type` ( `to_char_type` ( *x* ) ) == *x*

pour Any `int_type` *x*et

`to_char_type` ( `to_int_type` ( *x* ) ) == *x*

pour tout `char_type` *x*.

### <a name="example"></a>Exemple

```cpp
// char_traits_to_int_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   char_traits<char>::char_type ch1 = 'a';
   char_traits<char>::char_type ch2 = 'b';
   char_traits<char>::char_type ch3 = 'a';

   // Converting from char_type to int_type
   char_traits<char>::int_type int1, int2 , int3;
   int1 =char_traits<char>:: to_int_type ( ch1 );
   int2 =char_traits<char>:: to_int_type ( ch2 );
   int3 =char_traits<char>:: to_int_type ( ch3 );

   cout << "The char_types and corresponding int_types are:"
        << "\n    ch1 = " << ch1 << " corresponding to int1 = "
        << int1 << "."
        << "\n    ch2 = " << ch2 << " corresponding to int1 = "
        << int2 << "."
        << "\n    ch3 = " << ch3 << " corresponding to int1 = "
        << int3 << "." << endl << endl;

   // Converting from int_type back to char_type
   char_traits<char>::char_type rec_ch1;
   rec_ch1 = char_traits<char>:: to_char_type ( int1);
   char_traits<char>::char_type rec_ch2;
   rec_ch2 = char_traits<char>:: to_char_type ( int2);

   cout << "The recovered char_types and corresponding int_types are:"
        << "\n    recovered ch1 = " << rec_ch1 << " from int1 = "
        << int1 << "."
        << "\n    recovered ch2 = " << rec_ch2 << " from int2 = "
        << int2 << "." << endl << endl;

   // Testing that the conversions are inverse operations
   bool b1 = char_traits<char>::eq ( rec_ch1 , ch1 );
   if ( b1 )
      cout << "The recovered char_type of ch1"
           << " is equal to the original ch1." << endl;
   else
      cout << "The recovered char_type of ch1"
           << " is not equal to the original ch1." << endl;

   // An equivalent and alternatively test procedure
   if ( rec_ch2 == ch2 )
      cout << "The recovered char_type of ch2"
           << " is equal to the original ch2." << endl;
   else
      cout << "The recovered char_type of ch2"
           << " is not equal to the original ch2." << endl;
}
```

```Output
The char_types and corresponding int_types are:
    ch1 = a corresponding to int1 = 97.
    ch2 = b corresponding to int1 = 98.
    ch3 = a corresponding to int1 = 97.

The recovered char_types and corresponding int_types are:
    recovered ch1 = a from int1 = 97.
    recovered ch2 = b from int2 = 98.

The recovered char_type of ch1 is equal to the original ch1.
The recovered char_type of ch2 is equal to the original ch2.
```

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
