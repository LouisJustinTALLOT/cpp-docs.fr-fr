---
title: time_put, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xloctime/std::time_put
- locale/std::time_put::char_type
- locale/std::time_put::iter_type
- locale/std::time_put::do_put
- locale/std::time_put::put
dev_langs:
- C++
helpviewer_keywords:
- std::time_put [C++]
- std::time_put [C++], char_type
- std::time_put [C++], iter_type
- std::time_put [C++], do_put
- std::time_put [C++], put
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27a200ba94be8c4937342820fadf89e4225ba97d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719951"
---
# <a name="timeput-class"></a>time_put, classe

Cette classe de modèle décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions des valeurs temporelles en séquences de type `CharType`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>Paramètres

*CharType*<br/>
Type utilisé dans le cadre d'un programme pour encoder des caractères.

*OutputIterator*<br/>
Type d'itération dans lequel les fonctions put temporelles enregistrent leur sortie.

## <a name="remarks"></a>Notes

Comme avec n'importe quelle facette de paramètres régionaux, l'ID d'objet statique possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans **id.**

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[time_put](#time_put)|Constructeur des objets de type `time_put`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.|
|[iter_type](#iter_type)|Type qui décrit un itérateur de sortie.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[do_put](#do_put)|Fonction virtuelle qui fournit en sortie des informations de date et d'heure sous la forme d'une séquence d'objets `CharType`.|
|[put](#put)|Fournit en sortie des informations de date et d'heure sous la forme d'une séquence d'objets `CharType`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="char_type"></a>  time_put::char_type

Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `CharType`.

## <a name="do_put"></a>  time_put::do_put

Fonction virtuelle qui fournit en sortie des informations de date et d'heure sous la forme d'une séquence d'objets `CharType`.

```cpp
virtual iter_type do_put(
    iter_type next,
    ios_base& _Iosbase,
    const tm* _Pt,
    char _Fmt,
    char _Mod = 0) const;
```

### <a name="parameters"></a>Paramètres

*next*<br/>
Itérateur de sortie indiquant où la séquence de caractères représentant la date et l’heure doivent être insérés.

*_Iosbase*<br/>
Non utilisé.

*_Pt*<br/>
Les informations de date et d’heure fournies en sortie.

*_Fmt*<br/>
Le format de la sortie. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.

*_Mod*<br/>
Un modificateur du format. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.

### <a name="return-value"></a>Valeur de retour

Un itérateur pour la première position après le dernier élément inséré.

### <a name="remarks"></a>Notes

La fonction membre protégée virtuelle génère des éléments séquentiels en commençant à `next` à partir de valeurs d’heure stockées dans l’objet \* `_Pt`, de type `tm`. La fonction retourne un itérateur désignant l’emplacement suivant où insérer un élément au-delà de la sortie générée.

La sortie est générée par les mêmes règles utilisées par `strftime`, avec un dernier argument *_Pt*, pour la génération d’une série de **char** éléments dans un tableau. Chacun de ces **char** élément est supposé être mappé à un élément équivalent de type `CharType` par un simple mappage un à un. Si *_Mod* est égal à zéro, le format efficace est « %f », où F est remplacé par *_Fmt*. Sinon, le format efficace est « %MF », où M est remplacé par *_Mod*.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [put](#put), qui appelle `do_put`.

## <a name="iter_type"></a>  time_put::iter_type

Type qui décrit un itérateur de sortie.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `OutputIterator`.

## <a name="put"></a>  time_put::put

Fournit en sortie des informations de date et d'heure sous la forme d'une séquence d'objets `CharType`.

```cpp
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

*next*<br/>
Itérateur de sortie indiquant où la séquence de caractères représentant la date et l’heure doivent être insérés.

*_Iosbase*<br/>
Non utilisé.

*_Fill*<br/>
Le caractère de type `CharType` utilisé pour l’espacement.

*_Pt*<br/>
Les informations de date et d’heure fournies en sortie.

*_Fmt*<br/>
Le format de la sortie. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.

*_Mod*<br/>
Un modificateur du format. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.

*first*<br/>
Le début de la chaîne de mise en forme pour la sortie. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.

*last*<br/>
La fin de la chaîne de mise en forme pour la sortie. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.

### <a name="return-value"></a>Valeur de retour

Un itérateur pour la première position après le dernier élément inséré.

### <a name="remarks"></a>Notes

La première fonction membre retourne [do_put](#do_put)(`next`, `_Iosbase`, `_Fill`, `_Pt`, `_Fmt`, `_Mod`). La seconde fonction membre copie dans \* `next` ++ n’importe quel élément figurant dans l’intervalle [ `first`, `last`) autre qu’un pour cent (%). Pour un pour cent suivi d’un caractère *C* dans l’intervalle [ `first`, `last`), la fonction évalue à la place `next` = `do_put`( `next`, `_Iosbase`, `_Fill`, `_Pt`, *C*, 0) et ignore *C*. Si, toutefois, *C* est un caractère de qualificateur issu de l’ensemble QEC#, suivi d’un caractère `C2` dans l’intervalle [ `first`, `last`), la fonction évalue à la place `next` = `do_put`( `next`, `_Iosbase`, `_Fill`, `_Pt`, `C2`, *C*) et ignore `C2`.

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

## <a name="time_put"></a>  time_put::time_put

Constructeur d’objets de type `time_put`.

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Paramètres

*_Refs*<br/>
Valeur entière utilisée pour spécifier le type de gestion de mémoire pour l’objet.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le *_Refs* paramètre et leur signification sont :

- 0 : la durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : la durée de vie de l’objet doit être gérée manuellement.

- \> 1 : ces valeurs ne sont pas définies.

Le constructeur initialise son objet de base avec [locale::facet](../standard-library/locale-class.md#facet_class)(*_Refs*).

## <a name="see-also"></a>Voir aussi

[\<locale>](../standard-library/locale.md)<br/>
[time_base, classe](../standard-library/time-base-class.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
