---
title: '&lt;string&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- string/std::operator!=
- string/std::operator&gt;
- string/std::operator&gt;&gt;
- string/std::operator&gt;=
- string/std::operator&lt;
- string/std::operator&lt;&lt;
- string/std::operator&lt;=
- string/std::operator+
- string/std::operator==
ms.assetid: 33ce8f05-06c7-45d3-a0cb-bcd27cf93910
helpviewer_keywords:
- std::operator!= (string)
- std::operator&gt; (string)
- std::operator&gt;&gt; (string)
- std::operator&gt;= (string)
- std::operator&lt; (string)
- std::operator&lt;&lt; (string)
- std::operator&lt;= (string), std::operator== (string)
ms.openlocfilehash: bb66e7c0120da9f140ce33da7ecc61299a4d2867
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459260"
---
# <a name="ltstringgt-operators"></a>&lt;string&gt;, opérateurs

||||
|-|-|-|
|[!=, opérateur](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;&gt;](#op_gt_gt)|
|[operator&gt;=](#op_gt_eq)|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|
|[operator&lt;=](#op_lt_eq)|[operator+](#op_add)|[operator==](#op_eq_eq)|

## <a name="op_add"></a>  operator+

Concatène deux objets string.

```cpp
template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const CharType left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    CharType right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    CharType left,
    const basic_string<CharType, Traits, Allocator>&& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Chaîne de style C ou objet de type `basic_string` à concaténer.

*Oui*\
Chaîne de style C ou objet de type `basic_string` à concaténer.

### <a name="return-value"></a>Valeur de retour

Chaîne qui est la concaténation des chaînes d'entrée.

### <a name="remarks"></a>Notes

Les fonctions surchargent toutes `operator+` pour concaténer deux objets de classe de modèle [basic_string](../standard-library/basic-string-class.md). Tout retourne `basic_string< CharType, Traits, Allocator>(Left).append(right)`effectivement. Pour plus d’informations, consultez [Append](../standard-library/basic-string-class.md#append).

### <a name="example"></a>Exemple

```cpp
// string_op_con.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an object of type basic_string<char>
   string s1 ( "anti" );
   string s2 ( "gravity" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "heroine";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // Declaring a character constant
   char c1 = '!';
   cout << "The character constant c1 = " << c1 << "." << endl;

   // First member function: concatenates an  object
   // of type basic_string with an object of type basic_string
   string s12 = s1 + s2;
   cout << "The string concatenating s1 & s2 is: " << s12 << endl;

   // Second & fourth member functions: concatenate an object
   // of type basic_string with an object of C-syle string type
   string s1s3 = s1 + s3;
   cout << "The string concatenating s1 & s3 is: " << s1s3 << endl;

   // Third & fifth member functions: concatenate an object
   // of type basic_string with a character constant
   string s1s3c1 = s1s3 + c1;
   cout << "The string concatenating s1 & s3 is: " << s1s3c1 << endl;
}
```

```Output
The basic_string s1 = anti.
The basic_string s2 = gravity.
The C-style string s3 = heroine.
The character constant c1 = !.
The string concatenating s1 & s2 is: antigravity
The string concatenating s1 & s3 is: antiheroine
The string concatenating s1 & s3 is: antiheroine!
```

## <a name="op_neq"></a>  operator!=

Teste si l'objet string situé à gauche de l'opérateur n'est pas égal à l'objet string situé à droite.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator!=(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator!=(
    const basic_string<CharType, Traits, Allocator>& left,
const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator!=(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Chaîne de style C ou objet de type `basic_string` à comparer.

*Oui*\
Chaîne de style C ou objet de type `basic_string` à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet string situé à gauche de l’opérateur n’est pas égal du point de vue lexicographique à l’objet string situé à droite ; sinon, **false**.

### <a name="remarks"></a>Notes

La comparaison entre les objets string est basée sur une comparaison lexicographique par paire de leurs caractères. Deux chaînes sont égales si elles ont le même nombre de caractères et que les valeurs respectives de leurs caractères sont identiques. Sinon, elles sont inégales.

### <a name="example"></a>Exemple

```cpp
// string_op_ne.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "pluck" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "pluck";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 != s2 )
      cout << "The strings s1 & s2 are not equal." << endl;
   else
      cout << "The strings s1 & s2 are equal." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s1 != s3 )
      cout << "The strings s1 & s3 are not equal." << endl;
   else
      cout << "The strings s1 & s3 are equal." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s3 != s2 )
      cout << "The strings s3 & s2 are not equal." << endl;
   else
      cout << "The strings s3 & s2 are equal." << endl;
}
```

```Output
The basic_string s1 = pluck.
The basic_string s2 = strum.
The C-style string s3 = pluck.
The strings s1 & s2 are not equal.
The strings s1 & s3 are equal.
The strings s3 & s2 are not equal.
```

## <a name="op_eq_eq"></a>  operator==

Teste si l'objet string situé à gauche de l'opérateur est égal à l'objet string situé à droite.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator==(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator==(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator==(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Chaîne de style C ou objet de type `basic_string` à comparer.

*Oui*\
Chaîne de style C ou objet de type `basic_string` à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet string situé à gauche de l’opérateur est égal du point de vue lexicographique à l’objet string situé à droite ; sinon, **false**.

### <a name="remarks"></a>Notes

La comparaison entre les objets string est basée sur une comparaison lexicographique par paire de leurs caractères. Deux chaînes sont égales si elles ont le même nombre de caractères et que les valeurs respectives de leurs caractères sont identiques. Sinon, elles sont inégales.

### <a name="example"></a>Exemples

```cpp
// string_op_eq.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "pluck" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "pluck";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 == s2 )
      cout << "The strings s1 & s2 are equal." << endl;
   else
      cout << "The strings s1 & s2 are not equal." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s1 == s3 )
      cout << "The strings s1 & s3 are equal." << endl;
   else
      cout << "The strings s1 & s3 are not equal." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s3 == s2 )
      cout << "The strings s3 & s2 are equal." << endl;
   else
      cout << "The strings s3 & s2 are not equal." << endl;
}
```

```Output
The basic_string s1 = pluck.
The basic_string s2 = strum.
The C-style string s3 = pluck.
The strings s1 & s2 are not equal.
The strings s1 & s3 are equal.
The strings s3 & s2 are not equal.
```

## <a name="op_lt"></a>  operator&lt;

Teste si l'objet string situé à gauche de l'opérateur est inférieur à l'objet string situé à droite.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator<(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator<(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator<(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Chaîne de style C ou objet de type `basic_string` à comparer.

*Oui*\
Chaîne de style C ou objet de type `basic_string` à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet string situé à gauche de l’opérateur est inférieur du point de vue lexicographique à l’objet string situé à droite ; sinon, **false**.

### <a name="remarks"></a>Notes

Une comparaison lexicographique entre des chaînes les compare caractère par caractère jusqu’à ce que :

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a>Exemples

```cpp
// string_op_lt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "strict";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 < s2 )
      cout << "The string s1 is less than the string s2." << endl;
   else
      cout << "The string s1 is not less than the string s2." << endl;

   // Second member function: comparison between left-hand object
   // of type basic_string & right-hand object of C-syle string type
   if ( s1 < s3 )
      cout << "The string s1 is less than the string s3." << endl;
   else
      cout << "The string s1 is not less than the string s3." << endl;

   // Third member function: comparison between left-hand object
   // of C-syle string type & right-hand object of type basic_string
   if ( s3 < s2 )
      cout << "The string s3 is less than the string s2." << endl;
   else
      cout << "The string s3 is not less than the string s2." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = strict.
The string s1 is less than the string s2.
The string s1 is not less than the string s3.
The string s3 is less than the string s2.
```

## <a name="op_lt_eq"></a>  operator&lt;=

Teste si l'objet string situé à gauche de l'opérateur est inférieur ou égal à l'objet string situé à droite.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator<=(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator<=(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator<=(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Chaîne de style C ou objet de type `basic_string` à comparer.

*Oui*\
Chaîne de style C ou objet de type `basic_string` à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet string situé à gauche de l’opérateur est inférieur ou égal du point de vue lexicographique à l’objet string situé à droite ; sinon, **false**.

### <a name="remarks"></a>Notes

Une comparaison lexicographique entre des chaînes les compare caractère par caractère jusqu’à ce que :

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a>Exemple

```cpp
// string_op_le.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "strict";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 <= s2 )
      cout << "The string s1 is less than or equal to "
           << "the string s2." << endl;
   else
      cout << "The string s1 is greater than "
           << "the string s2." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s1 <= s3 )
      cout << "The string s1 is less than or equal to "
           << "the string s3." << endl;
   else
      cout << "The string s1 is greater than "
           << "the string s3." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type  & right-side object of type basic_string
   if ( s2 <= s3 )
      cout << "The string s2 is less than or equal to "
           << "the string s3." << endl;
   else
      cout << "The string s2 is greater than "
           << "the string s3." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = strict.
The string s1 is less than or equal to the string s2.
The string s1 is less than or equal to the string s3.
The string s2 is greater than the string s3.
```

## <a name="op_lt_lt"></a>  operator&lt;&lt;

Fonction de modèle qui écrit une chaîne dans le flux de sortie.

```cpp
template <class CharType, class Traits, class Allocator>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& _Ostr,
    const basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>Paramètres

*_Ostr*\
Flux de sortie dans lequel s’effectue l’écriture.

*Str*\
Chaîne à entrer dans le flux de sortie.

### <a name="return-value"></a>Valeur de retour

Écrit la valeur de la chaîne spécifiée dans le flux de sortie *_Ostr*.

### <a name="remarks"></a>Notes

L’opérateur de fonction de modèle Overloads **< <** pour insérer un objet *Str* de la classe de modèle [basic_string](../standard-library/basic-string-class.md) dans le  *\_OSTR*de flux. La fonction retourne effectivement `_Ostr.write( str.c_str, str.size )`la valeur.

## <a name="op_gt"></a>  operator&gt;

Teste si l'objet string situé à gauche de l'opérateur est supérieur à l'objet string situé à droite.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator>(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator>(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator>(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Chaîne de style C ou objet de type `basic_string` à comparer.

*Oui*\
Chaîne de style C ou objet de type `basic_string` à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet string situé à gauche de l’opérateur est supérieur du point de vue lexicographique à l’objet string situé à droite ; sinon, **false**.

### <a name="remarks"></a>Notes

Une comparaison lexicographique entre des chaînes les compare caractère par caractère jusqu’à ce que :

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a>Exemple

```cpp
// string_op_gt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "stricture";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 > s2 )
      cout << "The string s1 is greater than "
           << "the string s2." << endl;
   else
      cout << "The string s1 is not greater than "
           << "the string s2." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s3 > s1 )
      cout << "The string s3 is greater than "
           << "the string s1." << endl;
   else
      cout << "The string s3 is not greater than "
           << "the string s1." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s2 > s3 )
      cout << "The string s2 is greater than "
           << "the string s3." << endl;
   else
      cout << "The string s2 is not greater than "
           << "the string s3." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = stricture.
The string s1 is not greater than the string s2.
The string s3 is greater than the string s1.
The string s2 is greater than the string s3.
```

## <a name="op_gt_eq"></a>  operator&gt;=

Teste si l'objet string situé à gauche de l'opérateur est supérieur ou égal à l'objet string situé à droite.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator>=(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator>=(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator>=(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Chaîne de style C ou objet de type `basic_string` à comparer.

*Oui*\
Chaîne de style C ou objet de type `basic_string` à comparer.

### <a name="return-value"></a>Valeur de retour

**true** si l’objet string situé à gauche de l’opérateur est supérieur ou égal du point de vue lexicographique à l’objet string situé à droite ; sinon, **false**.

### <a name="remarks"></a>Notes

Une comparaison lexicographique entre des chaînes les compare caractère par caractère jusqu’à ce que :

- Elle trouve deux caractères correspondants inégaux et le résultat de leur comparaison est considéré comme étant le résultat de la comparaison entre les chaînes.

- Elle ne trouve aucune inégalité, mais une chaîne a plus de caractères que l’autre, et la chaîne la plus courte est considérée comme inférieure à la chaîne la plus longue.

- Elle ne trouve aucune inégalité et les chaînes ont le même nombre de caractères, si bien que les chaînes sont égales.

### <a name="example"></a>Exemple

```cpp
// string_op_ge.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "stricture";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 >= s2 )
      cout << "The string s1 is greater than or equal to "
           << "the string s2." << endl;
   else
      cout << "The string s1 is less than "
           << "the string s2." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s3 >= s1 )
      cout << "The string s3 is greater than or equal to "
           << "the string s1." << endl;
   else
      cout << "The string s3 is less than "
           << "the string s1." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s2 >= s3 )
      cout << "The string s2 is greater than or equal to "
           << "the string s3." << endl;
   else
      cout << "The string s2 is less than "
           << "the string s3." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = stricture.
The string s1 is less than the string s2.
The string s3 is greater than or equal to the string s1.
The string s2 is greater than or equal to the string s3.
```

## <a name="op_gt_gt"></a>  operator&gt;&gt;

Fonction de modèle qui lit une chaîne à partir d’un flux d’entrée.

```cpp
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& operator>>(
    basic_istream<CharType, Traits>& _Istr,
    basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*_Istr*\
Le flux d’entrée utilisé pour extraire la séquence.

*Oui*\
La chaîne qui est extraite du flux d’entrée.

### <a name="return-value"></a>Valeur de retour

Lit la valeur de la chaîne spécifiée à partir de *_Istr* et la retourne à *droite*.

### <a name="remarks"></a>Notes

L’opérateur ignore les espaces blancs de début à moins que l’indicateur `skipws` soit défini. Il lit tous les caractères suivants jusqu’à ce que le caractère suivant soit un espace blanc ou que la fin du fichier soit atteinte.

L’opérateur de surcharge de fonction de modèle **> >** pour remplacer la séquence contrôlée par *Right* par une séquence d’éléments extraits du flux *_Istr*. L’extraction s’arrête :

- À la fin du fichier.

- Une fois que la fonction a extrait `_Istr`. **width** éléments, si cette valeur est différente de zéro.

Une fois que la fonction a extrait `_Istr`. [max_size](../standard-library/basic-string-class.md#max_size) éléments.

- Une fois que la fonction a extrait un élément *ch* pour lequel [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype**\< **CharType**> >( `getloc`). **is**( **ctype**\< **CharType**>:: **space**, *ch*) a la valeur true, auquel cas le caractère est replacé.

Si la fonction n’extrait aucun élément, elle appelle [SetState](../standard-library/basic-ios-class.md#setstate)(`ios_base::failbit`). Dans tous les cas, elle appelle **istr**. **width**(0) et retourne \* **this**.

### <a name="example"></a>Exemple

```cpp
// string_op_read_.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string c0;
   cout << "Input a string c0 ( try: Fibonacci numbers ): ";
   cin >> c0;
   cout << "The string entered is c0 = " << c0 << endl;
}
```

## <a name="see-also"></a>Voir aussi

[\<string>](../standard-library/string.md)
