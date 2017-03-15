---
title: '&lt;locale&gt;, fonctions | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b06c1ceb-33a7-48d3-8d4b-2714bbb27f14
caps.latest.revision: 15
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 5ca6c94270b97f8b6e48871699628415e2133778
ms.lasthandoff: 02/24/2017

---
# <a name="ltlocalegt-functions"></a>&lt;locale&gt;, fonctions
||||  
|-|-|-|  
|[has_facet](#has_facet)|[isalnum](#isalnum)|[isalpha](#isalpha)|  
|[iscntrl](#iscntrl)|[isdigit](#isdigit)|[isgraph](#isgraph)|  
|[islower](#islower)|[isprint](#isprint)|[ispunct](#ispunct)|  
|[isspace](#isspace)|[isupper](#isupper)|[isxdigit](#isxdigit)|  
|[tolower](#tolower)|[toupper](#toupper)|[use_facet](#use_facet)|  
  
##  <a name="a-namehasfaceta--hasfacet"></a><a name="has_facet"></a>  has_facet  
 Teste si une facette particulière est stockée dans des paramètres régionaux spécifiés.  
  
```  
template <class Facet>  
bool has_facet(const locale& Loc);
```  
  
### <a name="parameters"></a>Paramètres  
 `Loc`  
 Paramètres régionaux pour lesquels tester la présence d’une facette.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si les paramètres régionaux ont la facette testée ; **false** dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
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
  
##  <a name="a-nameisalnuma--isalnum"></a><a name="isalnum"></a>  isalnum  
 Teste si un élément figurant dans des paramètres régionaux est un caractère alphabétique ou numérique.  
  
```  
template <class CharType>  
bool isalnum(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Paramètres  
 `Ch`  
 Élément alphanumérique à tester.  
  
 `Loc`  
 Paramètres régionaux contenant l’élément alphanumérique à tester.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’élément testé est alphanumérique ; **false** dans le cas contraire.  
  
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
  
##  <a name="a-nameisalphaa--isalpha"></a><a name="isalpha"></a>  isalpha  
 Teste si un élément figurant dans des paramètres régionaux est un caractère alphabétique.  
  
```  
template <class CharType>  
bool isalpha(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Paramètres  
 `Ch`  
 Élément à tester.  
  
 `Loc`  
 Paramètres régionaux contenant l’élément alphabétique à tester.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’élément testé est alphabétique ; **false** dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [is](../standard-library/ctype-class.md#ctype__is)( **ctype**\< **CharType**>:: **alpha**, `Ch`).  
  
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
  
##  <a name="a-nameiscntrla--iscntrl"></a><a name="iscntrl"></a>  iscntrl  
 Teste si un élément figurant dans des paramètres régionaux est un caractère de contrôle.  
  
```  
template <class CharType>  
bool iscntrl(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Paramètres  
 `Ch`  
 Élément à tester.  
  
 `Loc`  
 Paramètres régionaux contenant l’élément à tester.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’élément testé est un caractère de contrôle ; **false** dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [is](../standard-library/ctype-class.md#ctype__is)( **ctype**\< **CharType**>:: **cntrl**, `Ch`).  
  
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
  
##  <a name="a-nameisdigita--isdigit"></a><a name="isdigit"></a>  isdigit  
 Teste si un élément figurant dans des paramètres régionaux est un caractère numérique.  
  
```  
template <class CharType>  
bool isdigit(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Paramètres  
 `Ch`  
 Élément à tester.  
  
 `Loc`  
 Paramètres régionaux contenant l’élément à tester.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’élément testé est un caractère numérique ; **false** dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [is](../standard-library/ctype-class.md#ctype__is)( **ctype**\< **CharType**>:: **digit**, `Ch`).  
  
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
  
##  <a name="a-nameisgrapha--isgraph"></a><a name="isgraph"></a>  isgraph  
 Teste si un élément figurant dans des paramètres régionaux est un caractère alphanumérique ou de ponctuation.  
  
```  
template <class CharType>  
bool isgraph(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Paramètres  
 `Ch`  
 Élément à tester.  
  
 `Loc`  
 Paramètres régionaux contenant l’élément à tester.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’élément testé est un caractère alphanumérique ou de ponctuation ; **false** dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [is](../standard-library/ctype-class.md#ctype__is)( **ctype**\< **CharType**>:: **graph**, `Ch`).  
  
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
  
##  <a name="a-nameislowera--islower"></a><a name="islower"></a>  islower  
 Teste si un élément figurant dans des paramètres régionaux est en minuscules.  
  
```  
template <class CharType>  
bool islower(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Paramètres  
 `Ch`  
 Élément à tester.  
  
 `Loc`  
 Paramètres régionaux contenant l’élément à tester.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’élément testé est un caractère minuscule ; **false** dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [is](../standard-library/ctype-class.md#ctype__is)( **ctype**\< **CharType**>:: **lower**, `Ch`).  
  
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
  
##  <a name="a-nameisprinta--isprint"></a><a name="isprint"></a>  isprint  
 Teste si un élément figurant dans des paramètres régionaux est un caractère imprimable.  
  
```  
template <class CharType>  
bool isprint(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Paramètres  
 `Ch`  
 Élément à tester.  
  
 `Loc`  
 Paramètres régionaux contenant l’élément à tester.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’élément testé est un caractère imprimable ; **false** dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [is](../standard-library/ctype-class.md#ctype__is)( **ctype**\< **CharType**>:: **print**, `Ch`).  
  
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
  
##  <a name="a-nameispuncta--ispunct"></a><a name="ispunct"></a>  ispunct  
 Teste si un élément figurant dans des paramètres régionaux est un caractère de ponctuation.  
  
```  
template <class CharType>  
bool ispunct(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Paramètres  
 `Ch`  
 Élément à tester.  
  
 `Loc`  
 Paramètres régionaux contenant l’élément à tester.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’élément testé est un caractère de ponctuation ; **false** dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet)`<`[ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [is](../standard-library/ctype-class.md#ctype__is)( **ctype**\< **CharType**>:: **punct**, `Ch`).  
  
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
  
##  <a name="a-nameisspacea--isspace"></a><a name="isspace"></a>  isspace  
 Teste si un élément figurant dans des paramètres régionaux est un espace blanc.  
  
```  
template <class CharType>  
bool isspace(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Paramètres  
 `Ch`  
 Élément à tester.  
  
 `Loc`  
 Paramètres régionaux contenant l’élément à tester.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’élément testé est un espace blanc ; **false** dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [is](../standard-library/ctype-class.md#ctype__is)( **ctype**\< **CharType**>:: **space**, `Ch`).  
  
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
  
##  <a name="a-nameisuppera--isupper"></a><a name="isupper"></a>  isupper  
 Teste si un élément figurant dans des paramètres régionaux est en majuscules.  
  
```  
template <class CharType>  
bool isupper(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Paramètres  
 `Ch`  
 Élément à tester.  
  
 `Loc`  
 Paramètres régionaux contenant l’élément à tester.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’élément testé est un caractère majuscule ; **false** dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [is](../standard-library/ctype-class.md#ctype__is)( **ctype**\< **CharType**>:: **upper**, `Ch`).  
  
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
  
##  <a name="a-nameisxdigita--isxdigit"></a><a name="isxdigit"></a>  isxdigit  
 Teste si un élément figurant dans des paramètres régionaux est un caractère utilisé pour représenter un nombre hexadécimal.  
  
```  
template <class CharType>  
bool isxdigit(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Paramètres  
 `Ch`  
 Élément à tester.  
  
 `Loc`  
 Paramètres régionaux contenant l’élément à tester.  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si l’élément testé est un caractère utilisé pour représenter un nombre hexadécimal ; **false** dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [is](../standard-library/ctype-class.md#ctype__is)( **ctype**\< **CharType**>:: **xdigit**, `Ch`).  
  
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
  
##  <a name="a-nametolowera--tolower"></a><a name="tolower"></a>  tolower  
 Convertit un caractère en minuscule.  
  
```  
template <class CharType>  
CharType tolower(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Paramètres  
 `Ch`  
 Caractère à convertir en minuscules.  
  
 `Loc`  
 Paramètres régionaux contenant le caractère à convertir.  
  
### <a name="return-value"></a>Valeur de retour  
 Caractère converti en minuscules.  
  
### <a name="remarks"></a>Remarques  
 La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [tolower](../standard-library/ctype-class.md#ctype__tolower)( `Ch`).  
  
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
  
##  <a name="a-nametouppera--toupper"></a><a name="toupper"></a>  toupper  
 Convertit un caractère en majuscule.  
  
```  
template <class CharType>  
CharType toupper(CharType Ch, const locale& Loc)  
```  
  
### <a name="parameters"></a>Paramètres  
 `Ch`  
 Caractère à convertir en majuscules.  
  
 `Loc`  
 Paramètres régionaux contenant le caractère à convertir.  
  
### <a name="return-value"></a>Valeur de retour  
 Caractère converti en majuscules.  
  
### <a name="remarks"></a>Remarques  
 La fonction de modèle retourne [use_facet](../standard-library/locale-functions.md#use_facet)< [ctype](../standard-library/ctype-class.md)\< **CharType**> >( `Loc`). [toupper](../standard-library/ctype-class.md#ctype__toupper)( `Ch`).  
  
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
  
##  <a name="a-nameusefaceta--usefacet"></a><a name="use_facet"></a>  use_facet  
 Retourne une référence à une facette d'un type spécifié stocké dans des paramètres régionaux.  
  
```  
template <class Facet>  
const Facet& use_facet(const locale& Loc);
```  
  
### <a name="parameters"></a>Paramètres  
 `Loc`  
 Paramètres régionaux const contenant le type de facette référencé.  
  
### <a name="return-value"></a>Valeur de retour  
 Référence à la facette de classe `Facet` contenue dans les paramètres régionaux d’argument.  
  
### <a name="remarks"></a>Remarques  
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


