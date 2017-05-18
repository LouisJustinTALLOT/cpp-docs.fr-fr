---
title: time_put, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- time_put
- xloctime/std::time_put
- locale/std::time_put::char_type
- locale/std::time_put::iter_type
- locale/std::time_put::do_put
- locale/std::time_put::put
dev_langs:
- C++
helpviewer_keywords:
- time_put class
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 0331580941a30b8d6ab9468ce95182950478ddcb
ms.contentlocale: fr-fr
ms.lasthandoff: 04/29/2017

---
# <a name="timeput-class"></a>time_put, classe
Cette classe de modèle décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions des valeurs temporelles en séquences de type `CharType`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class CharType,  
    class OutputIterator = ostreambuf_iterator<CharType>>  
class time_put : public locale::facet;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `CharType`  
 Type utilisé dans le cadre d'un programme pour encoder des caractères.  
  
 `OutputIterator`  
 Type d'itération dans lequel les fonctions put temporelles enregistrent leur sortie.  
  
## <a name="remarks"></a>Notes  
 Comme avec n'importe quelle facette de paramètres régionaux, l'ID d'objet statique possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans **id.**  
  
### <a name="constructors"></a>Constructeurs  
  
|||  
|-|-|  
|[time_put](#time_put)|Constructeur des objets de type `time_put`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.|  
|[iter_type](#iter_type)|Type qui décrit un itérateur de sortie.|  
  
### <a name="member-functions"></a>Fonctions membres  
  
|||  
|-|-|  
|[do_put](#do_put)|Fonction virtuelle qui fournit en sortie des informations de date et d'heure sous la forme d'une séquence d'objets `CharType`.|  
|[put](#put)|Fournit en sortie des informations de date et d'heure sous la forme d'une séquence d'objets `CharType`.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<locale>  
  
 **Espace de noms :** std  
  
##  <a name="char_type"></a>  time_put::char_type  
 Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle **CharType**.  
  
##  <a name="do_put"></a>  time_put::do_put  
 Fonction virtuelle qui fournit en sortie des informations de date et d’heure sous la forme d’une séquence de données **CharType**.  
  
```  
virtual iter_type do_put(
    iter_type next,   
    ios_base& _Iosbase,  
    const tm* _Pt,   
    char _Fmt,   
    char _Mod = 0) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `next`  
 Itérateur de sortie indiquant où la séquence de caractères représentant la date et l’heure doivent être insérés.  
  
 `_Iosbase`  
 Non utilisé.  
  
 `_Pt`  
 Les informations de date et d’heure fournies en sortie.  
  
 `_Fmt`  
 Le format de la sortie. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.  
  
 `_Mod`  
 Un modificateur du format. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur pour la première position après le dernier élément inséré.  
  
### <a name="remarks"></a>Notes  
 La fonction membre protégée virtuelle génère des éléments séquentiels en commençant à `next` à partir des valeurs d’heure stockées dans l’objet \* `_Pt`, de type **tm**. La fonction retourne un itérateur désignant l’emplacement suivant où insérer un élément au-delà de la sortie générée.  
  
 La sortie est générée par les mêmes règles utilisées par `strftime`, avec un dernier argument `_Pt`, pour générer une série d’éléments `char` dans un tableau. Chacun de ces éléments `char` est supposé être mappé à un élément équivalent de type **CharType** par un mappage « un à un » simple. Si `_Mod` est égal à zéro, le format efficace est « %F », où F est remplacé par `_Fmt`. Sinon, le format efficace est « %MF », où M est remplacé par `_Mod`.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple relatif à [put](#put), qui appelle `do_put`.  
  
##  <a name="iter_type"></a>  time_put::iter_type  
 Type qui décrit un itérateur de sortie.  
  
```  
typedef OutputIterator iter_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type est un synonyme du paramètre de modèle **OutputIterator**.  
  
##  <a name="put"></a>  time_put::put  
 Fournit en sortie des informations de date et d’heure sous la forme d’une séquence de données **CharType**.  
  
```  
iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;

iter_type put(iter_type next,
    ios_base& _Iosbase,
    char_type _Fill,
    const tm* _Pt,
    const CharType* first,
    const CharType* last) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `next`  
 Itérateur de sortie indiquant où la séquence de caractères représentant la date et l’heure doivent être insérés.  
  
 `_Iosbase`  
 Non utilisé.  
  
 `_Fill`  
 Le caractère de type **CharType** utilisé pour l’espacement.  
  
 `_Pt`  
 Les informations de date et d’heure fournies en sortie.  
  
 `_Fmt`  
 Le format de la sortie. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.  
  
 `_Mod`  
 Un modificateur du format. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.  
  
 `first`  
 Le début de la chaîne de mise en forme pour la sortie. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.  
  
 `last`  
 La fin de la chaîne de mise en forme pour la sortie. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur pour la première position après le dernier élément inséré.  
  
### <a name="remarks"></a>Notes  
 La première fonction membre retourne [do_put](#do_put)( `next`, `_Iosbase`, `_Fill`, `_Pt`, `_Fmt`, `_Mod`). La seconde fonction membre copie dans \* `next` ++ n’importe quel élément figurant dans l’intervalle [ `first`, `last`) autre qu’un pour cent (%). Pour un pour cent suivi d’un caractère *C* dans l’intervalle [ `first`, `last`), la fonction évalue à la place `next` = `do_put`( `next`, `_Iosbase`, `_Fill`, `_Pt`, *C*, 0) et ignore *C*. Si, toutefois, *C* est un caractère de qualificateur issu de l’ensemble QEC#, suivi d’un caractère `C2` dans l’intervalle [ `first`, `last`), la fonction évalue à la place `next` = `do_put`( `next`, `_Iosbase`, `_Fill`, `_Pt`, `C2`, *C*) et ignore `C2`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// time_put_put.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
#include <time.h>  
using namespace std;  
int main( )  
{  
   locale loc;  
   basic_stringstream<char> pszPutI;  
   ios_base::iostate st = 0;  
   struct tm t;  
   memset( &t, 0, sizeof( struct tm ) );  
  
   t.tm_hour = 5;  
   t.tm_min = 30;  
   t.tm_sec = 40;  
   t.tm_year = 00;  
   t.tm_mday = 4;  
   t.tm_mon = 6;  
  
   pszPutI.imbue( loc );  
   char *pattern = "x: %X %x";  
   use_facet <time_put <char> >  
   (loc).put(basic_ostream<char>::_Iter(pszPutI.rdbuf( )),  
          pszPutI, ' ', &t, pattern, pattern+strlen(pattern));  
  
      cout << "num_put( ) = " << pszPutI.rdbuf( )->str( ) << endl;  
  
      char strftimebuf[255];  
      strftime(&strftimebuf[0], 255, pattern, &t);  
      cout << "strftime( ) = " << &strftimebuf[0] << endl;  
}  
```  
  
```Output  
num_put( ) = x: 05:30:40 07/04/00  
strftime( ) = x: 05:30:40 07/04/00  
```  
  
##  <a name="time_put"></a>  time_put::time_put  
 Constructeur d’objets de type `time_put`.  
  
```  
explicit time_put(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Refs`  
 Valeur entière utilisée pour spécifier le type de gestion de mémoire pour l’objet.  
  
### <a name="remarks"></a>Notes  
 Les valeurs possibles pour le paramètre `_Refs` et leur signification sont les suivantes :  
  
-   0 : la durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.  
  
-   1 : la durée de vie de l’objet doit être gérée manuellement.  
  
-   \>1 : ces valeurs ne sont pas définis.  
  
 Le constructeur initialise l’objet de base avec [locale::facet](../standard-library/locale-class.md#facet_class)(*_Refs*).  
  
## <a name="see-also"></a>Voir aussi  
 [\<locale>](../standard-library/locale.md)   
 [time_base, classe](../standard-library/time-base-class.md)   
 [Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)


