---
description: En savoir plus sur les &lt; fonctions de paramètres régionaux &gt;
title: '&lt;locale&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- locale/std::has_facet
- locale/std::isalnum
- locale/std::isalpha
- locale/std::iscntrl
- locale/std::isdigit
- locale/std::isgraph
- locale/std::islower
- locale/std::isprint
- locale/std::ispunct
- locale/std::isspace
- locale/std::isupper
- locale/std::isxdigit
- locale/std::tolower
- locale/std::toupper
- locale/std::use_facet
ms.assetid: b06c1ceb-33a7-48d3-8d4b-2714bbb27f14
helpviewer_keywords:
- std::has_facet [C++]
- std::isalnum [C++]
- std::isalpha [C++]
- std::iscntrl [C++]
- std::isdigit [C++]
- std::isgraph [C++]
- std::islower [C++]
- std::isprint [C++]
- std::ispunct [C++]
- std::isspace [C++]
- std::isupper [C++]
- std::isxdigit [C++]
- std::tolower [C++]
- std::toupper [C++]
- std::use_facet [C++]
ms.openlocfilehash: 6bad3cab6886fcee34fba06e88ce54e216db4649
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284614"
---
# <a name="ltlocalegt-functions"></a>&lt;locale&gt;, fonctions

[has_facet](#has_facet)\
[isalnum](#isalnum)\
[isalpha](#isalpha)\
[iscntrl](#iscntrl)\
[IsDigit](#isdigit)\
[isgraph](#isgraph)\
[IsLower](#islower)\
[isprint](#isprint)\
[ispunct](#ispunct)\
[isspace](#isspace)\
[IsUpper](#isupper)\
[isxdigit](#isxdigit)\
[ToLower](#tolower)\
[ToUpper](#toupper)\
[use_facet](#use_facet)

## <a name="has_facet"></a><a name="has_facet"></a> has_facet

Teste si une facette particulière est stockée dans des paramètres régionaux spécifiés.

```cpp
template <class Facet>
bool has_facet(const locale& Loc);
```

### <a name="parameters"></a>Paramètres

*Loc*\
Paramètres régionaux pour lesquels tester la présence d’une facette.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si les paramètres régionaux ont la facette testée pour ; **`false`** si ce n’est pas le cas.

### <a name="remarks"></a>Notes

La fonction de modèle est utile pour vérifier si des facettes non obligatoires sont répertoriées dans des paramètres régionaux avant que `use_facet` soit appelée, pour éviter l’exception qui serait levée s’ils n’étaient pas présents.

### <a name="example"></a>Exemple

```cpp
// locale_has_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result = has_facet <ctype<char> > ( loc );
   cout << result << endl;
}
```

```Output
1
```

## <a name="isalnum"></a><a name="isalnum"></a> isalnum

Teste si un élément figurant dans des paramètres régionaux est un caractère alphabétique ou numérique.

```cpp
template <class CharType>
bool isalnum(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Paramètres

*Cascade*\
Élément alphanumérique à tester.

*Loc*\
Paramètres régionaux contenant l’élément alphanumérique à tester.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’élément testé est alphanumérique ; **`false`** si ce n’est pas le cas.

### <a name="example"></a>Exemple

```cpp
// locale_isalnum.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalnum ( 'L', loc);
   bool result2 = isalnum ( '@', loc);
   bool result3 = isalnum ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphanumeric." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphanumeric." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphanumeric." << endl;
}
```

```Output
The character 'L' in the locale is alphanumeric.
The character '@' in the locale is  not alphanumeric.
The character '3' in the locale is alphanumeric.
```

## <a name="isalpha"></a><a name="isalpha"></a> isalpha

Teste si un élément figurant dans des paramètres régionaux est un caractère alphabétique.

```cpp
template <class CharType>
bool isalpha(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Paramètres

*Cascade*\
Élément à tester.

*Loc*\
Paramètres régionaux contenant l’élément alphabétique à tester.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’élément testé est alphabétique ; **`false`** si ce n’est pas le cas.

### <a name="remarks"></a>Notes

La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [est](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **alpha**, `Ch` ).

### <a name="example"></a>Exemple

```cpp
// locale_isalpha.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalpha ( 'L', loc);
   bool result2 = isalpha ( '@', loc);
   bool result3 = isalpha ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphabetic." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphabetic." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphabetic." << endl;
}
```

## <a name="iscntrl"></a><a name="iscntrl"></a> iscntrl

Teste si un élément figurant dans des paramètres régionaux est un caractère de contrôle.

```cpp
template <class CharType>
bool iscntrl(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Paramètres

*Cascade*\
Élément à tester.

*Loc*\
Paramètres régionaux contenant l’élément à tester.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’élément testé est un caractère de contrôle ; **`false`** si ce n’est pas le cas.

### <a name="remarks"></a>Notes

La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [est](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **CTRL**, `Ch` ).

### <a name="example"></a>Exemple

```cpp
// locale_iscntrl.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = iscntrl ( 'L', loc );
   bool result2 = iscntrl ( '\n', loc );
   bool result3 = iscntrl ( '\t', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a control character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a control character." << endl;

   if ( result2 )
      cout << "The character-set 'backslash-n' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale\n is "
           << " not a control character." << endl;

   if ( result3 )
      cout << "The character-set 'backslash-t' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale \n is "
           << " not a control character." << endl;
}
```

## <a name="isdigit"></a><a name="isdigit"></a> IsDigit

Teste si un élément figurant dans des paramètres régionaux est un caractère numérique.

```cpp
template <class CharType>
bool isdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Paramètres

*Cascade*\
Élément à tester.

*Loc*\
Paramètres régionaux contenant l’élément à tester.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’élément testé est un caractère numérique ; **`false`** si ce n’est pas le cas.

### <a name="remarks"></a>Notes

La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [est](../standard-library/ctype-class.md#is)de ( **CType** \< **CharType**> :: **digit**, `Ch` ).

### <a name="example"></a>Exemple

```cpp
// locale_is_digit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isdigit ( 'L', loc );
   bool result2 = isdigit ( '@', loc );
   bool result3 = isdigit ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a numeric character." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not a numeric character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a numeric character." << endl;
}
```

## <a name="isgraph"></a><a name="isgraph"></a> isgraph

Teste si un élément figurant dans des paramètres régionaux est un caractère alphanumérique ou de ponctuation.

```cpp
template <class CharType>
bool isgraph(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Paramètres

*Cascade*\
Élément à tester.

*Loc*\
Paramètres régionaux contenant l’élément à tester.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’élément testé est un caractère alphanumérique ou de ponctuation ; **`false`** si ce n’est pas le cas.

### <a name="remarks"></a>Notes

La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [est](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Graph**, `Ch` ).

### <a name="example"></a>Exemple

```cpp
// locale_is_graph.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isgraph ( 'L', loc );
   bool result2 = isgraph ( '\t', loc );
   bool result3 = isgraph ( '.', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;

   if ( result2 )
      cout << "The character 'backslash-t' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is\n "
           << "not an alphanumeric or punctuation character." << endl;

   if ( result3 )
      cout << "The character '.' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character '.' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;
}
```

## <a name="islower"></a><a name="islower"></a> IsLower

Teste si un élément figurant dans des paramètres régionaux est en minuscules.

```cpp
template <class CharType>
bool islower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Paramètres

*Cascade*\
Élément à tester.

*Loc*\
Paramètres régionaux contenant l’élément à tester.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’élément testé est un caractère minuscule ; **`false`** si ce n’est pas le cas.

### <a name="remarks"></a>Notes

La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [est](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Lower**, `Ch` ).

### <a name="example"></a>Exemple

```cpp
// locale_islower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = islower ( 'L', loc );
   bool result2 = islower ( 'n', loc );
   bool result3 = islower ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a lowercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a lowercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a lowercase character." << endl;
}
```

## <a name="isprint"></a><a name="isprint"></a> isprint

Teste si un élément figurant dans des paramètres régionaux est un caractère imprimable.

```cpp
template <class CharType>
bool isprint(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Paramètres

*Cascade*\
Élément à tester.

*Loc*\
Paramètres régionaux contenant l’élément à tester.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’élément testé est un imprimable ; **`false`** si ce n’est pas le cas.

### <a name="remarks"></a>Notes

La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [est](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Print**, `Ch` ).

### <a name="example"></a>Exemple

```cpp
// locale_isprint.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );

   bool result1 = isprint ( 'L', loc );
   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a printable character." << endl;

   bool result2 = isprint( '\t', loc );
   if ( result2 )
      cout << "The character 'backslash-t' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is "
           << " not a printable character." << endl;

   bool result3 = isprint( '\n', loc );
   if ( result3 )
      cout << "The character 'backslash-n' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a printable character." << endl;
}
```

## <a name="ispunct"></a><a name="ispunct"></a> ispunct

Teste si un élément figurant dans des paramètres régionaux est un caractère de ponctuation.

```cpp
template <class CharType>
bool ispunct(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Paramètres

*Cascade*\
Élément à tester.

*Loc*\
Paramètres régionaux contenant l’élément à tester.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’élément testé est un caractère de ponctuation ; **`false`** si ce n’est pas le cas.

### <a name="remarks"></a>Notes

La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet) `<` [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [est](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **punct**, `Ch` ).

### <a name="example"></a>Exemple

```cpp
// locale_ispunct.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = ispunct ( 'L', loc );
   bool result2 = ispunct ( ';', loc );
   bool result3 = ispunct ( '*', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a punctuation character." << endl;

   if ( result2 )
      cout << "The character ';' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character ';' in the locale is "
           << " not a punctuation character." << endl;

   if ( result3 )
      cout << "The character '*' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character '*' in the locale is "
           << " not a punctuation character." << endl;
}
```

## <a name="isspace"></a><a name="isspace"></a> isspace

Teste si un élément figurant dans des paramètres régionaux est un espace blanc.

```cpp
template <class CharType>
bool isspace(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Paramètres

*Cascade*\
Élément à tester.

*Loc*\
Paramètres régionaux contenant l’élément à tester.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’élément testé est un caractère d’espace blanc ; **`false`** si ce n’est pas le cas.

### <a name="remarks"></a>Notes

La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [est](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Space**, `Ch` ).

### <a name="example"></a>Exemple

```cpp
// locale_isspace.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isspace ( 'L', loc );
   bool result2 = isspace ( '\n', loc );
   bool result3 = isspace ( ' ', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a whitespace character." << endl;

   if ( result2 )
      cout << "The character 'backslash-n' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a whitespace character." << endl;

   if ( result3 )
      cout << "The character ' ' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character ' ' in the locale is "
           << " not a whitespace character." << endl;
}
```

## <a name="isupper"></a><a name="isupper"></a> IsUpper

Teste si un élément figurant dans des paramètres régionaux est en majuscules.

```cpp
template <class CharType>
bool isupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Paramètres

*Cascade*\
Élément à tester.

*Loc*\
Paramètres régionaux contenant l’élément à tester.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’élément testé est un caractère majuscule ; **`false`** si ce n’est pas le cas.

### <a name="remarks"></a>Notes

La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [est](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **Upper**, `Ch` ).

### <a name="example"></a>Exemple

```cpp
// locale_isupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isupper ( 'L', loc );
   bool result2 = isupper ( 'n', loc );
   bool result3 = isupper ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a uppercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a uppercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a uppercase character." << endl;
}
```

## <a name="isxdigit"></a><a name="isxdigit"></a> isxdigit

Teste si un élément figurant dans des paramètres régionaux est un caractère utilisé pour représenter un nombre hexadécimal.

```cpp
template <class CharType>
bool isxdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Paramètres

*Cascade*\
Élément à tester.

*Loc*\
Paramètres régionaux contenant l’élément à tester.

### <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’élément testé est un caractère utilisé pour représenter un nombre hexadécimal ; **`false`** si ce n’est pas le cas.

### <a name="remarks"></a>Notes

La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [est](../standard-library/ctype-class.md#is)( **CType** \< **CharType**> :: **xdigit**, `Ch` ).

Les chiffres hexadécimaux utilisent la base 16 pour représenter les nombres, en utilisant les nombres de 0 à 9 et les lettres de A à F (sans respect de la casse) pour représenter les nombres décimaux de 0 à 15.

### <a name="example"></a>Exemple

```cpp
// locale_isxdigit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isxdigit ( '5', loc );
   bool result2 = isxdigit ( 'd', loc );
   bool result3 = isxdigit ( 'q', loc );

   if ( result1 )
      cout << "The character '5' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character '5' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result2 )
      cout << "The character 'd' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'd' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result3 )
      cout << "The character 'q' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'q' in the locale is "
           << " not a hexidecimal digit-character." << endl;
}
```

## <a name="tolower"></a><a name="tolower"></a> ToLower

Convertit un caractère en minuscule.

```cpp
template <class CharType>
CharType tolower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Paramètres

*Cascade*\
Caractère à convertir en minuscule.

*Loc*\
Paramètres régionaux contenant le caractère à convertir.

### <a name="return-value"></a>Valeur renvoyée

Caractère converti en minuscules.

### <a name="remarks"></a>Notes

La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [ToLower](../standard-library/ctype-class.md#tolower)( `Ch` ).

### <a name="example"></a>Exemple

```cpp
// locale_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = tolower ( 'H', loc );
   cout << "The lower case of 'H' in the locale is: "
        << result1 << "." << endl;
   char result2 = tolower ( 'h', loc );
   cout << "The lower case of 'h' in the locale is: "
        << result2 << "." << endl;
   char result3 = tolower ( '$', loc );
   cout << "The lower case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="toupper"></a><a name="toupper"></a> ToUpper

Convertit un caractère en majuscule.

```cpp
template <class CharType>
CharType toupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>Paramètres

*Cascade*\
Caractère à convertir en majuscule.

*Loc*\
Paramètres régionaux contenant le caractère à convertir.

### <a name="return-value"></a>Valeur renvoyée

Caractère converti en majuscules.

### <a name="remarks"></a>Notes

La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet) <  [CType](../standard-library/ctype-class.md) \< **CharType**> > ( `Loc` ). [ToUpper](../standard-library/ctype-class.md#toupper)( `Ch` ).

### <a name="example"></a>Exemple

```cpp
// locale_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = toupper ( 'h', loc );
   cout << "The upper case of 'h' in the locale is: "
        << result1 << "." << endl;
   char result2 = toupper ( 'H', loc );
   cout << "The upper case of 'H' in the locale is: "
        << result2 << "." << endl;
   char result3 = toupper ( '$', loc );
   cout << "The upper case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="use_facet"></a><a name="use_facet"></a> use_facet

Retourne une référence à une facette d'un type spécifié stocké dans des paramètres régionaux.

```cpp
template <class Facet>
const Facet& use_facet(const locale& Loc);
```

### <a name="parameters"></a>Paramètres

*Loc*\
Paramètres régionaux const contenant le type de facette référencé.

### <a name="return-value"></a>Valeur renvoyée

Référence à la facette de classe `Facet` contenue dans les paramètres régionaux d’argument.

### <a name="remarks"></a>Notes

La référence à la facette retournée par la fonction de modèle reste valide tant qu’il existe une copie des paramètres régionaux contenants. Si aucun objet facette de classe `Facet` de ce type n’est répertorié dans les paramètres régionaux d’argument, la fonction lève une exception `bad_cast`.

### <a name="example"></a>Exemple

```cpp
// locale_use_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );
   bool result1 = use_facet<ctype<char> > ( loc1 ).is(
   ctype_base::alpha, 'a'
);
   bool result2 = use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!'
   );

   if ( result1 )
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if ( result2 )
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;
}
```

```Output
The character 'a' in locale loc1 is alphabetic.
The character '!' in locale loc2 is not alphabetic.
```

## <a name="see-also"></a>Voir aussi

[\<locale>](../standard-library/locale.md)
