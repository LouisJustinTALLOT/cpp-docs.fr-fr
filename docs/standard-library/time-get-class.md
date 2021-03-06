---
description: 'En savoir plus sur : classe time_get'
title: time_get, classe
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get
- locale/std::time_get::char_type
- locale/std::time_get::iter_type
- locale/std::time_get::date_order
- locale/std::time_get::do_date_order
- locale/std::time_get::do_get
- locale/std::time_get::do_get_date
- locale/std::time_get::do_get_monthname
- locale/std::time_get::do_get_time
- locale/std::time_get::do_get_weekday
- locale/std::time_get::do_get_year
- locale/std::time_get::get
- locale/std::time_get::get_date
- locale/std::time_get::get_monthname
- locale/std::time_get::get_time
- locale/std::time_get::get_weekday
- locale/std::time_get::get_year
helpviewer_keywords:
- std::time_get [C++]
- std::time_get [C++], char_type
- std::time_get [C++], iter_type
- std::time_get [C++], date_order
- std::time_get [C++], do_date_order
- std::time_get [C++], do_get
- std::time_get [C++], do_get_date
- std::time_get [C++], do_get_monthname
- std::time_get [C++], do_get_time
- std::time_get [C++], do_get_weekday
- std::time_get [C++], do_get_year
- std::time_get [C++], get
- std::time_get [C++], get_date
- std::time_get [C++], get_monthname
- std::time_get [C++], get_time
- std::time_get [C++], get_weekday
- std::time_get [C++], get_year
ms.assetid: 869d5f5b-dbab-4628-8333-bdea7e272023
ms.openlocfilehash: 079929d66ceb124fbceb1a908fbe9a868c446471
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167290"
---
# <a name="time_get-class"></a>time_get, classe

Le modèle de classe décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de séquences de type `CharType` en valeurs de temps.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>Paramètres

*CharType*\
Type utilisé dans le cadre d'un programme pour encoder des caractères.

*InputIterator*\
Itérateur dont les valeurs temporelles sont lues.

## <a name="remarks"></a>Notes

Comme avec n'importe quelle facette de paramètres régionaux, l'ID d'objet statique possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans **id.**

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[time_get](#time_get)|Constructeur des objets de type `time_get`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.|
|[iter_type](#iter_type)|Type qui décrit un itérateur d'entrée.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[date_order](#date_order)|Retourne l'ordre de date utilisé par une facette.|
|[do_date_order](#do_date_order)|Fonction membre virtuelle qui est appelée pour retourner l'ordre de date utilisé par une facette.|
|[do_get](#do_get)|Lit, puis convertit des données de caractères en valeur temporelle.|
|[do_get_date](#do_get_date)|Fonction membre virtuelle appelée pour analyser une chaîne représentant une date générée par le spécificateur `x` pour `strftime`.|
|[do_get_monthname](#do_get_monthname)|Fonction membre virtuelle appelée pour analyser une chaîne représentant le nom du mois.|
|[do_get_time](#do_get_time)|Fonction membre virtuelle appelée pour analyser une chaîne représentant une date générée par le spécificateur `X` pour `strftime`.|
|[do_get_weekday](#do_get_weekday)|Fonction membre virtuelle appelée pour analyser une chaîne représentant le nom du jour de la semaine.|
|[do_get_year](#do_get_year)|Fonction membre virtuelle appelée pour analyser une chaîne représentant le nom de l'année.|
|[get](#get)|Lit une source de données de caractères et convertit ces données en heure, puis stocke cette dernière dans un struct d'heure.|
|[get_date](#get_date)|Analyse une chaîne représentant la date générée par le spécificateur `x` pour `strftime`.|
|[get_monthname](#get_monthname)|Analyse une chaîne représentant le nom du mois.|
|[get_time](#get_time)|Analyse une chaîne représentant la date générée par le spécificateur `X` pour `strftime`.|
|[get_weekday](#get_weekday)|Analyse une chaîne représentant le nom du jour de la semaine.|
|[get_year](#get_year)|Analyse une chaîne représentant le nom de l'année.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<locale>

**Espace de noms :** std

## <a name="time_getchar_type"></a><a name="char_type"></a> time_get :: char_type

Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle **CharType**.

## <a name="time_getdate_order"></a><a name="date_order"></a> time_get ::d ate_order

Retourne l'ordre de date utilisé par une facette.

```cpp
dateorder date_order() const;
```

### <a name="return-value"></a>Valeur renvoyée

L’ordre de date utilisé par une facette.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_date_order](#do_date_order).

### <a name="example"></a>Exemple

```cpp
// time_get_date_order.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
void po( char *p )
{
   locale loc( p );

   time_get <char>::dateorder order = use_facet <time_get <char> >( loc ).date_order ( );
   cout << loc.name( );
   switch (order){
      case time_base::dmy: cout << "(day, month, year)" << endl;
      break;
      case time_base::mdy: cout << "(month, day, year)" << endl;
      break;
      case time_base::ydm: cout << "(year, day, month)" << endl;
      break;
      case time_base::ymd: cout << "(year, month, day)"<< endl;
      break;
      case time_base::no_order: cout << "(no_order)"<< endl;
      break;
   }
}

int main( )
{
   po( "C" );
   po( "german" );
   po( "English_Britain" );
}
```

```Output
C(month, day, year)
German_Germany.1252(day, month, year)
English_United Kingdom.1252(day, month, year)
```

## <a name="time_getdo_date_order"></a><a name="do_date_order"></a> time_get ::d o_date_order

Fonction membre virtuelle qui est appelée pour retourner l'ordre de date utilisé par une facette.

```cpp
virtual dateorder do_date_order() const;
```

### <a name="return-value"></a>Valeur renvoyée

L’ordre de date utilisé par une facette.

### <a name="remarks"></a>Notes

La fonction membre protégée virtuelle retourne une valeur de type **time_base::dateorder**, qui décrit l’ordre dans lequel les composants de date sont mis en correspondance par [do_get_date](#do_get_date). Dans cette implémentation, la valeur est **time_base::mdy**, qui correspond aux dates de la forme décembre 2, 1979.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [date_order](#date_order), qui appelle `do_date_order`.

## <a name="time_getdo_get"></a><a name="do_get"></a> time_get ::d o_get

Lit, puis convertit des données de caractères en valeur temporelle. Accepte un spécificateur et un modificateur de conversion.

```cpp
virtual iter_type
    do_get(
iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d'entrée qui indique le début de la séquence à convertir.

*famille*\
Itérateur d'entrée qui indique la fin de la séquence.

*iosbase*\
Objet de flux.

*Département*\
Champ dans iosbase où les éléments de masque binaire appropriés sont définis pour indiquer des erreurs.

*PTM*\
Pointeur vers la structure time, où l'heure doit être stockée.

*fmt*\
Caractère de spécificateur de conversion.

*modification*\
Caractère de modificateur facultatif.

### <a name="return-value"></a>Valeur renvoyée

Retourne un itérateur qui désigne le premier élément non converti. Un échec de conversion définit `ios_base::failbit` dans `state` et retourne en *premier*.

### <a name="remarks"></a>Notes

La fonction membre virtuelle convertit et ignore un ou plusieurs éléments d’entrée dans la plage [ `first` , `last` ) pour déterminer les valeurs stockées dans un ou plusieurs membres de `*pt` . Un échec de conversion définit `ios_base::failbit` dans `state` et retourne en *premier*. Sinon, la fonction retourne un itérateur désignant le premier élément non converti.

Les spécificateurs de conversion sont :

`'a'` ou `'A'` : se comporte comme [time_get::get_weekday](#get_weekday).

`'b'`, `'B'` ou `'h'` : se comporte comme [time_get::get_monthname](#get_monthname).

`'c'` : se comporte comme `"%b %d %H : %M : %S %Y"`.

`'C'` : convertit un champ d'entrée décimal dans la plage [0, 99] en valeur `val` et stocke `val * 100 - 1900` dans `pt-&tm_year`.

`'d'` ou `'e'` : convertit un champ d'entrée décimal dans la plage [1, 31] et stocke sa valeur dans `pt-&tm_mday`.

`'D'` : se comporte comme `"%m / %d / %y"`.

`'H'` : convertit un champ d'entrée décimal dans la plage [0, 23] et stocke sa valeur dans `pt-&tm_hour`.

`'I'` : convertit un champ d'entrée décimal dans la plage [0, 11] et stocke sa valeur dans `pt-&tm_hour`.

`'j'` : convertit un champ d'entrée décimal dans la plage [1, 366] et stocke sa valeur dans `pt-&tm_yday`.

`'m'` : convertit un champ d'entrée décimal dans la plage [1, 12] en valeur `val` et stocke sa valeur `val - 1` dans `pt-&tm_mon`.

`'M'` : convertit un champ d'entrée décimal dans la plage [0, 59] et stocke sa valeur dans `pt-&tm_min`.

`'n'` ou `'t'` : se comporte comme `" "`.

`'p'` : convertit « AM » ou « am » en zéro et « PM » ou « pm » en 12, et ajoute cette valeur à `pt-&tm_hour`.

`'r'` : se comporte comme `"%I : %M : %S %p"`.

`'R'` : se comporte comme `"%H %M"`.

`'S'` : convertit un champ d'entrée décimal dans la plage [0, 59] et stocke sa valeur dans `pt-&tm_sec`.

`'T'` ou `'X'` : se comporte comme `"%H : %M : S"`.

`'U'` : convertit un champ d'entrée décimal dans la plage [0, 53] et stocke sa valeur dans `pt-&tm_yday`.

`'w'` : convertit un champ d'entrée décimal dans la plage [0, 6] et stocke sa valeur dans `pt-&tm_wday`.

`'W'` : convertit un champ d'entrée décimal dans la plage [0, 53] et stocke sa valeur dans `pt-&tm_yday`.

`'x'` : se comporte comme `"%d / %m / %y"`.

`'y'` : convertit un champ d'entrée décimal dans la plage [0, 99] en valeur `val` et stocke `val < 69  val + 100 : val` dans `pt-&tm_year`.

`'Y'` : se comporte comme [time_get::get_year](#get_year).

Tous les autres spécificateurs de conversion définissent `ios_base::failbit` dans `state` et reviennent à l'appelant. Dans cette implémentation, les modificateurs n'ont pas d'effet.

## <a name="time_getdo_get_date"></a><a name="do_get_date"></a> time_get ::d o_get_date

Fonction membre protégée virtuelle appelée pour analyser une chaîne représentant une date générée par le spécificateur *x* pour `strftime`.

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’entrée traitant le début de la séquence à convertir.

*famille*\
Itérateur d’entrée traitant la fin de la séquence à convertir.

*iosbase*\
Indicateur de format qui, quand il est défini, indique que le symbole monétaire est facultatif. Dans le cas contraire, il est obligatoire.

*Département*\
Définit les éléments de masque de bits appropriés pour l’état de flux selon que les opérations ont réussi ou non.

*PTM*\
Pointeur vers l’emplacement où les informations de date doivent être stockées.

### <a name="return-value"></a>Valeur renvoyée

Itérateur d’entrée qui traite le premier élément au-delà du champ d’entrée.

### <a name="remarks"></a>Notes

La fonction membre protégée virtuelle tente de mettre en correspondance les éléments séquentiels en commençant par le premier dans la séquence [ `first`, `last`) jusqu’à ce qu’elle ait reconnu un champ d’entrée de date non vide, complet. En cas de réussite, elle convertit ce champ en sa valeur équivalente en tant que composants **TM :: TM \_ lun**, **TM :: TM \_ Day** et **TM :: TM \_ year**, et stocke les résultats dans `ptm->tm_mon` , `ptm->tm_day` et `ptm->tm_year` , respectivement. Elle retourne un itérateur désignant le premier élément au-delà du champ d’entrée de date. Dans le cas contraire, la fonction définit `iosbase::failbit` dans l' *État*. Elle retourne un itérateur désignant le premier élément au-delà de tout préfixe d’un champ d’entrée de date valide. Dans les deux cas, si la valeur de retour est égale à *Last*, la fonction définit `ios_base::eofbit` dans *State*.

Le format du champ d’entrée de date dépend des paramètres régionaux. Pour les paramètres régionaux par défaut, le champ d’entrée de date a la forme MMM JJ, AAAA, où :

- MMM est mis en correspondance en appelant [get_monthname](#get_monthname), ce qui donne le mois.

- JJ est une séquence de chiffres décimaux dont la valeur numérique correspondante doit être comprise dans la plage [1, 31], ce qui donne le jour du mois.

- AAAA est mis en correspondance en appelant [get_year](#get_year), ce qui donne l’année.

Les virgules et les espaces littéraux doivent correspondre aux éléments correspondants dans la séquence d’entrée.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [get_date](#get_date), qui appelle `do_get_date`.

## <a name="time_getdo_get_monthname"></a><a name="do_get_monthname"></a> time_get ::d o_get_monthname

Fonction membre virtuelle appelée pour analyser une chaîne représentant le nom du mois.

```cpp
virtual iter_type do_get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’entrée traitant le début de la séquence à convertir.

*famille*\
Itérateur d’entrée traitant la fin de la séquence à convertir.

*iosbase*\
Inutilisé.

*Département*\
Paramètre de sortie qui définit les éléments de masque de bits appropriés pour l’état de flux selon que les opérations ont réussi ou non.

*PTM*\
Pointeur vers l’emplacement où les informations de mois doivent être stockées.

### <a name="return-value"></a>Valeur renvoyée

Itérateur d’entrée qui traite le premier élément au-delà du champ d’entrée.

### <a name="remarks"></a>Notes

La fonction membre protégée virtuelle tente de mettre en correspondance les éléments séquentiels en commençant par le premier dans la séquence [ `first`, `last`) jusqu’à ce qu’elle ait reconnu un champ d’entrée de mois non vide, complet. En cas de réussite, elle convertit ce champ en sa valeur équivalente en tant que composant **TM :: TM \_ lun**, et stocke le résultat dans `ptm->tm_mon` . Elle retourne un itérateur désignant le premier élément au-delà du champ d’entrée de mois. Dans le cas contraire, la fonction définit `ios_base::failbit` dans l' *État*. Elle retourne un itérateur désignant le premier élément au-delà de tout préfixe d’un champ d’entrée de mois valide. Dans les deux cas, si la valeur de retour est égale à *Last*, la fonction définit `ios_base::eofbit` dans *State*.

Le champ d’entrée du mois est une séquence qui correspond à la plus longue séquence d’un ensemble de séquences spécifiques aux paramètres régionaux, telles que Jan, janvier, Fév, février, etc. La valeur convertie est le nombre de mois depuis janvier.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [get_monthname](#get_monthname), qui appelle `do_get_monthname`.

## <a name="time_getdo_get_time"></a><a name="do_get_time"></a> time_get ::d o_get_time

Fonction membre virtuelle protégée qui est appelée pour analyser une chaîne comme la date produite par le spécificateur *X* pour `strftime` .

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’entrée traitant le début de la séquence à convertir.

*famille*\
Itérateur d’entrée traitant la fin de la séquence à convertir.

*iosbase*\
Inutilisé.

*Département*\
Définit les éléments de masque de bits appropriés pour l’état de flux selon que les opérations ont réussi ou non.

*PTM*\
Pointeur vers l’emplacement où les informations de date doivent être stockées.

### <a name="return-value"></a>Valeur renvoyée

Itérateur d’entrée qui traite le premier élément au-delà du champ d’entrée.

### <a name="remarks"></a>Notes

La fonction membre protégée virtuelle tente de mettre en correspondance les éléments séquentiels en commençant par le premier dans la séquence [ `first`, `last`) jusqu’à ce qu’elle ait reconnu un champ d’entrée d’heure non vide, complet. En cas de réussite, elle convertit ce champ en sa valeur équivalente en tant que composants `tm::tm_hour` , `tm::tm_min` et, `tm::tm_sec` et stocke les résultats dans `ptm->tm_hour` , `ptm->tm_min` et `ptm->tm_sec` , respectivement. Elle retourne un itérateur désignant le premier élément au-delà du champ d’entrée d’heure. Dans le cas contraire, la fonction définit `ios_base::failbit` dans l' *État*. Elle retourne un itérateur désignant le premier élément au-delà de tout préfixe d’un champ d’entrée d’heure valide. Dans les deux cas, si la valeur de retour est égale à *Last*, la fonction définit `ios_base::eofbit` dans *State*.

Dans cette implémentation, le champ d’entrée d’heure a la forme HH:MM:SS, où :

- HH est une séquence de chiffres décimaux dont la valeur numérique correspondante doit être comprise dans la plage [0, 24], ce qui donne l’heure du jour.

- MM est une séquence de chiffres décimaux dont la valeur numérique correspondante doit être comprise dans la plage [0, 60], ce qui donne les minutes.

- SS est une séquence de chiffres décimaux dont la valeur numérique correspondante doit être comprise dans la plage [0, 60], ce qui donne les secondes.

Les deux-points littéraux doivent correspondre aux éléments correspondants dans la séquence d’entrée.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [get_time](#get_time), qui appelle `do_get_time`.

## <a name="time_getdo_get_weekday"></a><a name="do_get_weekday"></a> time_get ::d o_get_weekday

Fonction membre virtuelle appelée pour analyser une chaîne représentant le nom du jour de la semaine.

```cpp
virtual iter_type do_get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’entrée traitant le début de la séquence à convertir.

*famille*\
Itérateur d’entrée traitant la fin de la séquence à convertir.

*iosbase*\
Indicateur de format qui, quand il est défini, indique que le symbole monétaire est facultatif. Dans le cas contraire, il est obligatoire.

*Département*\
Définit les éléments de masque de bits appropriés pour l’état de flux selon que les opérations ont réussi ou non.

*PTM*\
Pointeur vers l’emplacement où les informations de jour de la semaine doivent être stockées.

### <a name="return-value"></a>Valeur renvoyée

Itérateur d’entrée qui traite le premier élément au-delà du champ d’entrée.

### <a name="remarks"></a>Notes

La fonction membre protégée virtuelle tente de faire correspondre des éléments séquentiels en commençant au *premier* dans la séquence [ `first` , `last` ) jusqu’à ce qu’elle ait reconnu un champ d’entrée de jour de la semaine non vide et complet. En cas de réussite, elle convertit ce champ en sa valeur équivalente en tant que composant **TM :: TM \_ WDAY** et stocke le résultat dans `ptm->tm_wday` . Elle retourne un itérateur désignant le premier élément au-delà du champ d’entrée de jour de la semaine. Dans le cas contraire, la fonction définit `ios_base::failbit` dans l' *État*. Elle retourne un itérateur désignant le premier élément au-delà de tout préfixe d’un champ d’entrée de jour de la semaine valide. Dans les deux cas, si la valeur de retour est égale à *Last*, la fonction définit `ios_base::eofbit` dans *State*.

Le champ d’entrée de jour de la semaine est une séquence qui correspond à la plus longue séquence d’un ensemble de séquences spécifiques aux paramètres régionaux, telles que Dim, Dimanche, Lun, Lundi, etc. La valeur convertie est le nombre de jours depuis Dimanche.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [get_weekday](#get_weekday), qui appelle `do_get_weekday`.

## <a name="time_getdo_get_year"></a><a name="do_get_year"></a> time_get ::d o_get_year

Fonction membre virtuelle appelée pour analyser une chaîne représentant le nom de l'année.

```cpp
virtual iter_type do_get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’entrée traitant le début de la séquence à convertir.

*famille*\
Itérateur d’entrée traitant la fin de la séquence à convertir.

*iosbase*\
Indicateur de format qui, quand il est défini, indique que le symbole monétaire est facultatif. Dans le cas contraire, il est obligatoire.

*Département*\
Définit les éléments de masque de bits appropriés pour l’état de flux selon que les opérations ont réussi ou non.

*PTM*\
Pointeur vers l’emplacement où les informations d’année doivent être stockées.

### <a name="return-value"></a>Valeur renvoyée

Itérateur d’entrée qui traite le premier élément au-delà du champ d’entrée.

### <a name="remarks"></a>Notes

La fonction membre protégée virtuelle tente de faire correspondre des éléments séquentiels en commençant au *premier* dans la séquence [ `first` , `last` ) jusqu’à ce qu’elle ait reconnu un champ d’entrée d’année non vide et complet. En cas de réussite, elle convertit ce champ en sa valeur équivalente en tant que composant **TM :: TM \_ year** et stocke le résultat dans `ptm->tm_year` . Elle retourne un itérateur désignant le premier élément au-delà du champ d’entrée d’année. Dans le cas contraire, la fonction définit `ios_base::failbit` dans l' *État*. Elle retourne un itérateur désignant le premier élément au-delà de tout préfixe d’un champ d’entrée d’année valide. Dans les deux cas, si la valeur de retour est égale à *Last*, la fonction définit `ios_base::eofbit` dans *State*.

Le champ d’entrée d’année est une séquence de chiffres décimaux dont la valeur numérique correspondante doit être comprise dans la plage [1900, 2036). La valeur stockée est égale à cette valeur moins 1900. Dans cette implémentation, les valeurs de la plage [69, 136) représentent la plage d’années [1969, 2036). Les valeurs de la plage [0, 69) sont également possibles, mais peuvent représenter la plage d’années [1900, 1969) ou [2000, 2069), selon l’environnement de traduction spécifique.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [get_year](#get_year), qui appelle `do_get_year`.

## <a name="time_getget"></a><a name="get"></a> time_get :: obtient

Lit une source de données de caractères et convertit ces données en heure, puis stocke cette dernière dans un struct d'heure. La première fonction accepte un spécificateur et un modificateur de conversion, la seconde en accepte plusieurs.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char_type* fmt_first,
    char_type* fmt_last) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d'entrée qui indique le début de la séquence à convertir.

*famille*\
Itérateur d'entrée qui indique la fin de la séquence à convertir.

*iosbase*\
Flux.

*Département*\
Les éléments du masque de bits appropriés sont définis pour l'état du flux et indiquent les erreurs.

*PTM*\
Pointeur vers la structure time, où la date/heure doit être stockée.

*fmt*\
Caractère de spécificateur de conversion.

*modification*\
Caractère de modificateur facultatif.

*fmt_first*\
Pointe là où les directives de format commencent.

*fmt_last*\
Pointe vers la fin des directives de format.

### <a name="return-value"></a>Valeur renvoyée

Retourne un itérateur au premier caractère après les données qui ont été utilisées pour assigner la structure d’heure `*ptm` .

### <a name="remarks"></a>Notes

La première fonction membre retourne `do_get(first, last, iosbase, state, ptm, fmt, mod)`.

La seconde fonction membre appelle `do_get` sous le contrôle du format délimité par `[fmt_first, fmt_last)`. Elle traite le format comme une séquence de champs, chacun d'entre eux déterminant la conversion de zéro ou plus entrées d'éléments, délimités par `[first, last)`. Elle retourne un itérateur qui désigne le premier élément non converti. Il existe trois types de champs :

A pour cent (%) dans le format, suivi d’un modificateur facultatif *dans l'* ensemble [EOQ #], suivi d’un spécificateur de conversion *fmt*, remplace d' *abord* par la valeur retournée par `do_get(first, last, iosbase, state, ptm, fmt, mod)` . Un échec de conversion définit `ios_base::failbit` dans l' *État* et retourne.

Un élément d'espace dans le format ignore zéro ou plus éléments d'espace d'entrée.

Tout autre élément dans le format doit correspondre à l'élément d'entrée suivant, qui est ignoré. Une erreur de correspondance définit `ios_base::failbit` l' *État* et retourne.

## <a name="time_getget_date"></a><a name="get_date"></a> time_get :: get_date

Analyse une chaîne représentant la date générée par le spécificateur *x* pour `strftime`.

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’entrée traitant le début de la séquence à convertir.

*famille*\
Itérateur d’entrée traitant la fin de la séquence à convertir.

*iosbase*\
Indicateur de format qui, quand il est défini, indique que le symbole monétaire est facultatif. Dans le cas contraire, il est obligatoire.

*Département*\
Définit les éléments de masque de bits appropriés pour l’état de flux selon que les opérations ont réussi ou non.

*PTM*\
Pointeur vers l’emplacement où les informations de date doivent être stockées.

### <a name="return-value"></a>Valeur renvoyée

Itérateur d’entrée qui traite le premier élément au-delà du champ d’entrée.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_get_date](#do_get_date)( `first` , `last` , `iosbase` , `state` , `ptm` ).

Notez que les mois sont numérotés de 0 à 11.

### <a name="example"></a>Exemple

```cpp
// time_get_get_date.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset(&t, 0, sizeof(struct tm));

   pszGetF << "July 4, 2000";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get<char> >
   (loc).get_date(basic_istream<char>::_Iter(pszGetF.rdbuf( ) ),
            basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if ( st & ios_base::failbit )
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(July 4, 2000) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 4
tm_mon: 6
tm_year: 100
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="time_getget_monthname"></a><a name="get_monthname"></a> time_get :: get_monthname

Analyse une chaîne représentant le nom du mois.

```cpp
iter_type get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’entrée traitant le début de la séquence à convertir.

*famille*\
Itérateur d’entrée traitant la fin de la séquence à convertir.

*iosbase*\
Inutilisé.

*Département*\
Paramètre de sortie qui définit les éléments de masque de bits appropriés pour l’état de flux selon que les opérations ont réussi ou non.

*PTM*\
Pointeur vers l’emplacement où les informations de mois doivent être stockées.

### <a name="return-value"></a>Valeur renvoyée

Itérateur d’entrée qui traite le premier élément au-delà du champ d’entrée.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_get_monthname](#do_get_monthname)( `first` , `last` , `iosbase` , `state` , `ptm` ).

### <a name="example"></a>Exemple

```cpp
// time_get_get_monthname.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "juillet";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get <char> >
   (loc).get_monthname(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
              basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(juillet) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 0
tm_mon: 6
tm_year: 0
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="time_getget_time"></a><a name="get_time"></a> time_get :: get_time

Analyse une chaîne en tant que date produite par le spécificateur *X* pour `strftime` .

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’entrée traitant le début de la séquence à convertir.

*famille*\
Itérateur d’entrée traitant la fin de la séquence à convertir.

*iosbase*\
Inutilisé.

*Département*\
Définit les éléments de masque de bits appropriés pour l’état de flux selon que les opérations ont réussi ou non.

*PTM*\
Pointeur vers l’emplacement où les informations de date doivent être stockées.

### <a name="return-value"></a>Valeur renvoyée

Itérateur d’entrée qui traite le premier élément au-delà du champ d’entrée.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_get_time](#do_get_time)( `first` , `last` , `iosbase` , `state` , `ptm` ).

### <a name="example"></a>Exemple

```cpp
// time_get_get_time.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "11:13:20";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get <char> >
      (loc).get_time(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << endl;
}
```

```Output
time_get::get_time(11:13:20) =
tm_sec: 20
tm_min: 13
tm_hour: 11
```

## <a name="time_getget_weekday"></a><a name="get_weekday"></a> time_get :: get_weekday

Analyse une chaîne représentant le nom du jour de la semaine.

```cpp
iter_type get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’entrée traitant le début de la séquence à convertir.

*famille*\
Itérateur d’entrée traitant la fin de la séquence à convertir.

*iosbase*\
Indicateur de format qui, quand il est défini, indique que le symbole monétaire est facultatif. Dans le cas contraire, il est obligatoire.

*Département*\
Définit les éléments de masque de bits appropriés pour l’état de flux selon que les opérations ont réussi ou non.

*PTM*\
Pointeur vers l’emplacement où les informations de jour de la semaine doivent être stockées.

### <a name="return-value"></a>Valeur renvoyée

Itérateur d’entrée qui traite le premier élément au-delà du champ d’entrée.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_get_weekday](#do_get_weekday)( `first` , `last` , `iosbase` , `state` , `ptm` ).

### <a name="example"></a>Exemple

```cpp
// time_get_get_weekday.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "mercredi";
   pszGetF.imbue(loc);
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_weekday(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_wday: " << t.tm_wday
      << endl;
}
```

```Output
time_get::get_time(mercredi) =
tm_wday: 3
```

## <a name="time_getget_year"></a><a name="get_year"></a> time_get :: get_year

Analyse une chaîne représentant le nom de l'année.

```cpp
iter_type get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Itérateur d’entrée traitant le début de la séquence à convertir.

*famille*\
Itérateur d’entrée traitant la fin de la séquence à convertir.

*iosbase*\
Indicateur de format qui, quand il est défini, indique que le symbole monétaire est facultatif. Dans le cas contraire, il est obligatoire.

*Département*\
Définit les éléments de masque de bits appropriés pour l’état de flux selon que les opérations ont réussi ou non.

*PTM*\
Pointeur vers l’emplacement où les informations d’année doivent être stockées.

### <a name="return-value"></a>Valeur renvoyée

Itérateur d’entrée qui traite le premier élément au-delà du champ d’entrée.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_get_year](#do_get_year)( `first` , `last` , `iosbase` , `state` , `ptm` ).

### <a name="example"></a>Exemple

```cpp
// time_get_get_year.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "1928";

   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_year(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_year: " << t.tm_year
      << endl;
}
```

```Output
time_get::get_year(1928) =
tm_year: 28
```

## <a name="time_getiter_type"></a><a name="iter_type"></a> time_get :: iter_type

Type qui décrit un itérateur d'entrée.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle **InputIterator**.

## <a name="time_gettime_get"></a><a name="time_get"></a> time_get :: time_get

Constructeur des objets de type `time_get`.

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>Paramètres

*Same*\
Valeur entière utilisée pour spécifier le type de gestion de mémoire pour l’objet.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le paramètre *REFS* et leur signification sont les suivantes :

- 0 : la durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : la durée de vie de l’objet doit être gérée manuellement.

- \> 1 : ces valeurs ne sont pas définies.

Aucun exemple direct n’est possible, car le destructeur est protégé.

Le constructeur initialise son objet de base avec **locale ::**[facette](../standard-library/locale-class.md#facet_class)( `refs` ).

## <a name="see-also"></a>Voir aussi

[\<locale>](../standard-library/locale.md)\
[Classe time_base](../standard-library/time-base-class.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
