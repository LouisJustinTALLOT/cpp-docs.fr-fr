---
title: time_put, classe
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put
- locale/std::time_put::char_type
- locale/std::time_put::iter_type
- locale/std::time_put::do_put
- locale/std::time_put::put
helpviewer_keywords:
- std::time_put [C++]
- std::time_put [C++], char_type
- std::time_put [C++], iter_type
- std::time_put [C++], do_put
- std::time_put [C++], put
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
ms.openlocfilehash: 10691de0a583dc7d5a66c319968d90978bf59480
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367997"
---
# <a name="time_put-class"></a>time_put, classe

Le modèle de classe décrit un objet qui peut servir de facette locale `CharType`pour contrôler les conversions des valeurs temporelles en séquences de type .

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class time_put : public locale::facet;
```

### <a name="parameters"></a>Paramètres

*CharType CharType*\
Type utilisé dans le cadre d'un programme pour encoder des caractères.

*Iterator De sortie*\
Type d'itération dans lequel les fonctions put temporelles enregistrent leur sortie.

## <a name="remarks"></a>Notes

Comme avec n'importe quelle facette de paramètres régionaux, l'ID d'objet statique possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans **id.**

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[time_put](#time_put)|Constructeur des objets de type `time_put`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.|
|[iter_type](#iter_type)|Type qui décrit un itérateur de sortie.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[do_put](#do_put)|Fonction virtuelle qui fournit en sortie des informations de date et d'heure sous la forme d'une séquence d'objets `CharType`.|
|[Mettre](#put)|Fournit en sortie des informations de date et d'heure sous la forme d'une séquence d'objets `CharType`.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="time_putchar_type"></a><a name="char_type"></a>time_put::char_type

Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `CharType`.

## <a name="time_putdo_put"></a><a name="do_put"></a>time_put::do-put

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

*prochain*\
Itérateur de sortie indiquant où la séquence de caractères représentant la date et l’heure doivent être insérés.

*_Iosbase*\
Inutilisé.

*_Pt*\
Les informations de date et d’heure fournies en sortie.

*_Fmt*\
Le format de la sortie. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.

*_Mod*\
Un modificateur du format. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.

### <a name="return-value"></a>Valeur de retour

Un itérateur pour la première position après le dernier élément inséré.

### <a name="remarks"></a>Notes

La fonction virtuelle protégée des membres génère `next` des éléments séquentiels à partir de la date des valeurs stockées dans l’objet, \* `_Pt`du type `tm`. La fonction retourne un itérateur désignant l’emplacement suivant où insérer un élément au-delà de la sortie générée.

La sortie est générée par `strftime`les mêmes règles utilisées par , avec un dernier argument de *_Pt*, pour générer une série d’éléments **char** dans un tableau. Chaque élément **de char** de ce genre `CharType` est supposé cartographier un élément équivalent de type par une cartographie simple et simple. Si *_Mod* égale zéro, le format efficace est "%F", où F est remplacé par *_Fmt*. Sinon, le format efficace est "%MF", où M est remplacé par *_Mod*.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [put](#put), qui appelle `do_put`.

## <a name="time_putiter_type"></a><a name="iter_type"></a>time_put::iter_type

Type qui décrit un itérateur de sortie.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `OutputIterator`.

## <a name="time_putput"></a><a name="put"></a>time_put::put

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

*prochain*\
Itérateur de sortie indiquant où la séquence de caractères représentant la date et l’heure doivent être insérés.

*_Iosbase*\
Inutilisé.

*_Fill*\
Le caractère `CharType` du type utilisé pour l’espacement.

*_Pt*\
Les informations de date et d’heure fournies en sortie.

*_Fmt*\
Le format de la sortie. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.

*_Mod*\
Un modificateur du format. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.

*Première*\
Le début de la chaîne de mise en forme pour la sortie. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.

*Dernière*\
La fin de la chaîne de mise en forme pour la sortie. Consultez [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) pour obtenir des valeurs valides.

### <a name="return-value"></a>Valeur de retour

Un itérateur pour la première position après le dernier élément inséré.

### <a name="remarks"></a>Notes

La première fonction de membre`next`revient `_Fill` `_Pt` [do_put](#do_put) `_Mod`( , `_Iosbase`, , , `_Fmt`. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . La fonction du \* `next` deuxième membre s’inso `last`quand même élément de l’intervalle [, `first`) autre qu’un pour cent (%). Pour un pour cent suivi d’un caractère *C* dans `next`  = l’intervalle `_Pt`[, `first`), `last`la fonction évalue plutôt `do_put` `next`( `_Iosbase`, `_Fill`, , *C*, 0) et saute passé *C*. Si, cependant, *C* est un personnage qualificatif de `C2` l’ensemble `first`EOQ, suivi d’un personnage dans l’intervalle [, `last`), la fonction évalue `next`  =  `do_put`plutôt ( `next`, `_Iosbase`, `_Fill`, `_Pt`, `C2` *C*) et saute passé `C2`.

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

## <a name="time_puttime_put"></a><a name="time_put"></a>time_put::time_put

Constructeur d’objets de type `time_put`.

```cpp
explicit time_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Paramètres

*_Refs*\
Valeur entière utilisée pour spécifier le type de gestion de mémoire pour l’objet.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le *_Refs* paramètre et leur signification sont les suivante :

- 0 : la durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : la durée de vie de l’objet doit être gérée manuellement.

- \>1: Ces valeurs ne sont pas définies.

Le constructeur initialise son objet de base avec [local:facet](../standard-library/locale-class.md#facet_class)(*_Refs*).

## <a name="see-also"></a>Voir aussi

[\<local>](../standard-library/locale.md)\
[Classe time_base](../standard-library/time-base-class.md)\
[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)
