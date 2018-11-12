---
title: locale, classe
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::locale
- xlocale/std::locale::category
- xlocale/std::locale::combine
- xlocale/std::locale::name
- xlocale/std::locale::classic
- xlocale/std::locale::global
- xlocale/std::locale::operator( )
- xlocale/std::locale::facet
- xlocale/std::locale::id
helpviewer_keywords:
- std::locale [C++]
- std::locale [C++], category
- std::locale [C++], combine
- std::locale [C++], name
- std::locale [C++], classic
- std::locale [C++], global
- std::locale [C++], facet
- std::locale [C++], id
ms.assetid: 7dd6d271-472d-4750-8fb5-ea8f55fbef62
ms.openlocfilehash: 888aeff3e8661338d1a017c06325108a4240ace3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677914"
---
# <a name="locale-class"></a>locale, classe

Classe qui décrit un objet de paramètres régionaux encapsulant des informations spécifiques à la culture sous la forme d'un ensemble de facettes qui définissent collectivement un environnement localisé spécifique.

## <a name="syntax"></a>Syntaxe

```cpp
class locale;
```

## <a name="remarks"></a>Notes

Une facette est un pointeur vers un objet d’une classe dérivée de la classe [facet](#facet_class) qui contient un objet public au format suivant :

```cpp
static locale::id id;
```

Vous pouvez définir un ensemble ouvert de ces facettes. Vous pouvez également créer un objet de paramètres régionaux qui désigne un nombre arbitraire de facettes.

Les groupes prédéfinis de ces facettes correspondent aux [catégories de paramètres régionaux](#category) traditionnellement gérées dans la bibliothèque C standard par la fonction `setlocale`.

La catégorie collate (LC_COLLATE) comprend les facettes suivantes :

```cpp
collate<char>
collate<wchar_t>
```

La catégorie ctype (LC_CTYPE) comprend les facettes suivantes :

```cpp
ctype<char>
ctype<wchar_t>
codecvt<char, char, mbstate_t>
codecvt<wchar_t, char, mbstate_t>
codecvt<char16_t, char, mbstate_t>
codecvt<char32_t, char, mbstate_t>
```

La catégorie monetary (LC_MONETARY) comprend les facettes suivantes :

```cpp
moneypunct<char, false>
moneypunct<wchar_t, false>
moneypunct<char, true>
moneypunct<wchar_t, true>
money_get<char, istreambuf_iterator<char>>
money_get<wchar_t, istreambuf_iterator<wchar_t>>
money_put<char, ostreambuf_iterator<char>>
money_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

La catégorie numeric (LC_NUMERIC) comprend les facettes suivantes :

```cpp
num_get<char, istreambuf_iterator<char>>
num_get<wchar_t, istreambuf_iterator<wchar_t>>
num_put<char, ostreambuf_iterator<char>>
num_put<wchar_t, ostreambuf_iterator<wchar_t>>
numpunct<char>
numpunct<wchar_t>
```

La catégorie time (LC_TIME) comprend les facettes suivantes :

```cpp
time_get<char, istreambuf_iterator<char>>
time_get<wchar_t, istreambuf_iterator<wchar_t>>
time_put<char, ostreambuf_iterator<char>>
time_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

La catégorie messages (LC_MESSAGES) comprend les facettes suivantes :

```cpp
messages<char>
messages<wchar_t>
```

La dernière catégorie est requise par Posix, mais pas par le C standard.

Certaines de ces facettes prédéfinies sont utilisées par les classes iostreams pour contrôler la conversion des valeurs numériques en séquences de texte, et inversement.

Un objet de classe locale stocke également un nom de paramètres régionaux en tant qu’objet de classe [string](../standard-library/string-typedefs.md#string). L’utilisation d’un nom de paramètres régionaux non valide pour construire une facette de paramètres régionaux ou un objet de paramètres régionaux entraîne la levée d’un objet de la classe [runtime_error](../standard-library/runtime-error-class.md). Le nom de paramètres régionaux stocké est `"*"` si l'objet de paramètres régionaux ne peut pas avoir la garantie que les paramètres régionaux de style C correspondent exactement à ceux représentés par l'objet. Sinon, vous pouvez créer des paramètres régionaux correspondants dans la bibliothèque C standard pour l’objet de paramètres régionaux `Loc`, en appelant `setlocale`(LC_ALL `,` `Loc`. [name](#name)`().c_str()`).

Dans cette implémentation, vous pouvez également appeler la fonction membre statique :

```cpp
static locale empty();
```

pour construire un objet de paramètres régionaux sans facette. Il s’agit également de paramètres régionaux transparents. Si les fonctions de modèle [has_facet](../standard-library/locale-functions.md#has_facet) et [use_facet](../standard-library/locale-functions.md#use_facet) ne trouvent pas la facette demandée dans les paramètres régionaux transparents, elles consultent d’abord les paramètres régionaux globaux puis, s’ils sont transparents, les paramètres régionaux classiques. Par conséquent, vous pouvez écrire :

```cpp
cout.imbue(locale::empty());
```

Les insertions ultérieures dans [cout](../standard-library/iostream.md#cout) sont atténuées par l’état actuel des paramètres régionaux globaux. Vous pouvez même écrire :

```cpp
locale loc(locale::empty(),
    locale::classic(),
    locale::numeric);

cout.imbue(loc);
```

Les règles de mise en forme numérique pour les insertions suivantes dans `cout` restent les mêmes que dans les paramètres régionaux du langage C, même lorsque les paramètres régionaux globaux fournissent des règles différentes d'insertion de dates et de valeurs monétaires.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[locale](#locale)|Crée des paramètres régionaux, une copie de paramètres régionaux ou une copie de paramètres régionaux où une facette ou une catégorie a été remplacée par une facette, ou une catégorie provenant d'autres paramètres régionaux.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[category](#category)|Type entier qui fournit des valeurs de masque de bits pour indiquer des familles de facettes standard.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[combine](#combine)|Insère une facette à partir des paramètres régionaux spécifiés dans les paramètres régionaux cibles.|
|[name](#name)|Retourne le nom des paramètres régionaux stocké.|

### <a name="static-functions"></a>Fonctions statiques

|||
|-|-|
|[classic](#classic)|La fonction membre statique retourne un objet de paramètres régionaux qui représente les paramètres régionaux classiques du langage C.|
|[global](#global)|Réinitialise les paramètres régionaux par défaut du programme.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[!=, opérateur](#op_neq)|Vérifie l'inégalité de deux ensembles de paramètres régionaux.|
|[operator( )](#op_call)|Compare deux objets `basic_string`.|
|[operator==](#op_eq_eq)|Vérifie l'égalité de deux ensembles de paramètres régionaux.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[facet](#facet_class)|Classe qui sert de classe de base pour toutes les facettes de paramètres régionaux.|
|[ID](#id_class)|La classe membre fournit un ID unique de facette utilisé comme index pour rechercher les facettes de paramètres régionaux.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="category"></a>  locale::category

Type entier qui fournit des valeurs de masque de bits pour indiquer des familles de facettes standard.

```cpp
typedef int category;
static const int collate = LC_COLLATE;
static const int ctype = LC_CTYPE;
static const int monetary = LC_MONETARY;
static const int numeric = LC_NUMERIC;
static const int time = LC_TIME;
static const int messages = LC_MESSAGES;
static const int all = LC_ALL;
static const int none = 0;
```

### <a name="remarks"></a>Notes

Le type est un synonyme pour un **int** tapez local à la classe de type qui peut représenter un groupe d’éléments distincts d’un masque de bits ou peut être utilisé pour représenter les catégories de paramètres régionaux C correspondantes. Les éléments sont :

- `collate`, correspondant à la catégorie C LC_COLLATE

- `ctype`, correspondant à la catégorie C LC_CTYPE

- `monetary`, correspondant à la catégorie C LC_MONETARY

- `numeric`, correspondant à la catégorie C LC_NUMERIC

- `time`, correspondant à la catégorie C LC_TIME

- `messages`, correspondant à la catégorie Posix LC_MESSAGES

En outre, les deux valeurs suivantes sont utiles :

- `none`, correspondant à aucune des catégories C

- `all`, correspondant à l’union C de toutes les catégories LC_ALL

Vous pouvez représenter un groupe arbitraire de catégories à l’aide de `OR` avec ces constantes, comme dans `monetary` &#124; `time`.

## <a name="classic"></a>  locale::classic

La fonction membre statique retourne un objet de paramètres régionaux qui représente les paramètres régionaux classiques du langage C.

```cpp
static const locale& classic();
```

### <a name="return-value"></a>Valeur de retour

Référence aux paramètres régionaux C.

### <a name="remarks"></a>Notes

Les paramètres régionaux C classiques sont les paramètres régionaux ASCII États-Unis Anglais dans la bibliothèque C standard qui sont implicitement utilisés dans les programmes qui ne sont pas internationalisés.

### <a name="example"></a>Exemple

```cpp
// locale_classic.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: " << loc2.name( )
        << "." << endl;
   cout << "The name of the current locale is: " << loc1.name( )
        << "." << endl;

   if (loc2 == locale::classic( ) )
      cout << "The previous locale was classic." << endl;
   else
      cout << "The previous locale was not classic." << endl;

   if (loc1 == locale::classic( ) )
      cout << "The current locale is classic." << endl;
   else
      cout << "The current locale is not classic." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
The previous locale was classic.
The current locale is not classic.
```

## <a name="combine"></a>  locale::combine

Insère une facette à partir des paramètres régionaux spécifiés dans les paramètres régionaux cibles.

```cpp
template <class Facet>
locale combine(const locale& Loc) const;
```

### <a name="parameters"></a>Paramètres

*Loc*<br/>
Paramètres régionaux contenant la facette à insérer dans les paramètres régionaux cibles.

### <a name="return-value"></a>Valeur de retour

La fonction membre retourne un objet de paramètres régionaux qui remplace ou ajoute à  **\*cela** la facette `Facet` répertoriés dans *Loc*.

### <a name="example"></a>Exemple

```cpp
// locale_combine.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s; it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   locale loc3 = loc2.combine<collate<_TCHAR> > (loc);
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;
}
```

## <a name="facet_class"></a> facet, classe

Classe qui sert de classe de base pour toutes les facettes de paramètres régionaux.

```cpp
class facet {
protected:
    explicit facet(size_t _Refs = 0);
   virtual ~facet();
private:
   facet(const facet&)
   // not defined void operator=(const facet&)
     // not defined
};
```

### <a name="remarks"></a>Notes

Notez que vous ne pouvez pas copier ou assigner un objet de la classe facette. Vous pouvez construire et détruire des objets dérivés de la classe `locale::facet`, mais pas des objets de la classe de base proprement dite. En règle générale, vous construisez un objet `_Myfac` dérivé de facet quand vous construisez des paramètres régionaux, comme dans **localeloc**( `locale::classic`( ), **new**`_Myfac`);

Dans ces cas-là, le constructeur de la classe de base facet doit avoir un argument `_Refs` égal à zéro. Quand l’objet n’est plus nécessaire, il est supprimé. Ainsi, vous fournissez un argument _ *Refs* différent de zéro uniquement dans les rares cas où vous prenez la responsabilité de la durée de vie de l’objet.

## <a name="global"></a>  locale::global

Réinitialise les paramètres régionaux par défaut du programme. Cela affecte les paramètres régionaux globaux pour C et C++.

```cpp
static locale global(const locale& Loc);
```

### <a name="parameters"></a>Paramètres

*Loc*<br/>
Paramètres régionaux à utiliser comme paramètres régionaux par défaut par le programme.

### <a name="return-value"></a>Valeur de retour

Paramètres régionaux en vigueur avant la réinitialisation des paramètres régionaux par défaut.

### <a name="remarks"></a>Notes

Au démarrage du programme, les paramètres régionaux globaux sont les mêmes que les paramètres régionaux classiques. La fonction `global()` appelle `setlocale( LC_ALL, loc.name. c_str())` pour déterminer les paramètres régionaux correspondants dans la bibliothèque C standard.

### <a name="example"></a>Exemple

```cpp
// locale_global.cpp
// compile by using: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   locale loc1;
   cout << "The initial locale is: " << loc1.name( ) << endl;
   locale loc2 = locale::global ( loc );
   locale loc3;
   cout << "The current locale is: " << loc3.name( ) << endl;
   cout << "The previous locale was: " << loc2.name( ) << endl;
}
```

```Output
The initial locale is: C
The current locale is: German_Germany.1252
The previous locale was: C
```

## <a name="id_class"></a>  id, classe

La classe membre fournit un ID unique de facette utilisé comme index pour rechercher les facettes de paramètres régionaux.

class id { protected:    id(); private:    id(const id&) // not defined void operator=(const id&)  // not defined    };

### <a name="remarks"></a>Notes

La classe membre décrit l’objet membre statique exigé par chaque facette de paramètres régionaux unique. Notez que vous ne pouvez pas copier ou assigner un objet de classe `id`.

## <a name="locale"></a>  locale::locale

Crée des paramètres régionaux, une copie de paramètres régionaux ou une copie de paramètres régionaux où une facette ou une catégorie a été remplacée par une facette, ou une catégorie provenant d'autres paramètres régionaux.

```cpp
locale();

explicit locale(const char* Locname, category Cat = all);
explicit locale(const string& Locname);
locale( const locale& Loc);
locale(const locale& Loc, const locale& Other, category Cat);
locale(const locale& Loc, const char* Locname, category Cat);

template <class Facet>
locale(const locale& Loc, const Facet* Fac);
```

### <a name="parameters"></a>Paramètres

*Locname*<br/>
Nom de paramètres régionaux.

*Loc*<br/>
Paramètres régionaux qui doivent être copiés lors de la construction des nouveaux paramètres régionaux.

*Autre*<br/>
Paramètres régionaux à partir desquels sélectionner une catégorie.

*CAT*<br/>
Catégorie à substituer dans les paramètres régionaux construits.

*Fac*<br/>
Facette à substituer dans les paramètres régionaux construits.

### <a name="remarks"></a>Notes

Le premier constructeur initialise l’objet pour qu’il corresponde aux paramètres régionaux globaux. Les deuxième et troisième constructeurs initialisent toutes les catégories de paramètres régionaux pour avoir un comportement cohérent avec le nom des paramètres régionaux *Locname*. Les autres constructeurs copient *Loc*, avec les exceptions notées :

`locale(const locale& Loc, const locale& Other, category Cat);`

remplace dans *autres* les facettes correspondant à une catégorie C pour lesquelles C & *Cat* est différent de zéro.

`locale(const locale& Loc, const char* Locname, category Cat);`

`locale(const locale& Loc, const string& Locname, category Cat);`

remplace dans `locale(Locname, _All)` les facettes correspondant à une catégorie C pour lesquelles C & *Cat* est différent de zéro.

`template<class Facet> locale(const locale& Loc, Facet* Fac);`

remplace dans (ou ajoute à) *Loc* la facette *Fac*si *Fac* n’est pas un pointeur null.

Si un nom de paramètres régionaux *Locname* est un pointeur null ou non valides, la fonction lève [runtime_error](../standard-library/runtime-error-class.md).

### <a name="example"></a>Exemple

```cpp
// locale_locale.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( ) {

   // Second constructor
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   // The first (default) constructor
   locale loc2;
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   // Third constructor
   locale loc3 (loc2,loc, _M_COLLATE );
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;

   // Fourth constructor
   locale loc4 (loc2, "German_Germany", _M_COLLATE );
   int result4 = use_facet<collate<_TCHAR> > ( loc4 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc4 ) << result4 << endl;
}
```

## <a name="name"></a>  locale::name

Retourne le nom des paramètres régionaux stocké.

```cpp
string name() const;
```

### <a name="return-value"></a>Valeur de retour

Chaîne indiquant le nom des paramètres régionaux.

### <a name="example"></a>Exemple

```cpp
// locale_name.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: "
        << loc2.name( ) << "." << endl;
   cout << "The name of the current locale is: "
        << loc1.name( ) << "." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
```

## <a name="op_neq"></a>  locale::operator!=

Vérifie l'inégalité de deux ensembles de paramètres régionaux.

```cpp
bool operator!=(const locale& right) const;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
L’un des paramètres régionaux dont l’inégalité doit être testée.

### <a name="return-value"></a>Valeur de retour

Valeur booléenne qui est **true** si les paramètres régionaux ne sont pas des copies des mêmes paramètres régionaux ; **false** si les paramètres régionaux sont des copies des mêmes paramètres régionaux.

### <a name="remarks"></a>Notes

Deux paramètres régionaux sont égaux s’ils s’agit des mêmes paramètres régionaux, si l’un est une copie de l’autre, ou s’ils ont des noms identiques.

### <a name="example"></a>Exemple

```cpp
// locale_op_ne.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 != loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are equal." << endl;

   if ( loc1 != loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are equal." << endl;
}
```

```Output
locales loc1 (German_Germany.1252) and
loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252) and
loc3 (English_United States.1252) are not equal.
```

## <a name="op_call"></a>  locale::operator()

Compare deux objets `basic_string`.

```cpp
template <class CharType, class Traits, class Allocator>
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right) const;
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Chaîne de gauche.

*right*<br/>
Chaîne de droite.

### <a name="return-value"></a>Valeur de retour

La fonction membre retourne :

- -1 si la première séquence est inférieure à la deuxième séquence.

- +1 si la deuxième séquence est inférieure à la première séquence.

- 0 si les séquences sont équivalentes.

### <a name="remarks"></a>Notes

La fonction de modèle exécute :

```cpp
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```

Ainsi, vous pouvez utiliser un objet de paramètres régionaux comme objet de fonction.

### <a name="example"></a>Exemple

```cpp
// locale_op_compare.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

int main( )
{
   using namespace std;
   wchar_t *sa = L"ztesting";
   wchar_t *sb = L"\0x00DFtesting";
   basic_string<wchar_t> a( sa );
   basic_string<wchar_t> b( sb );

   locale loc( "German_Germany" );
   cout << loc( a,b ) << endl;

   const collate<wchar_t>& fac = use_facet<collate<wchar_t> >( loc );
   cout << ( fac.compare( sa, sa + a.length( ),
       sb, sb + b.length( ) ) < 0) << endl;
}
```

```Output
0
0
```

## <a name="op_eq_eq"></a>  locale::operator==

Vérifie l'égalité de deux ensembles de paramètres régionaux.

```cpp
bool operator==(const locale& right) const;
```

### <a name="parameters"></a>Paramètres

*right*<br/>
L’un des paramètres régionaux dont l’égalité doit être testée.

### <a name="return-value"></a>Valeur de retour

Valeur booléenne qui est **true** si les paramètres régionaux sont des copies des mêmes paramètres régionaux ; **false** si les paramètres régionaux ne sont pas des copies des mêmes paramètres régionaux.

### <a name="remarks"></a>Notes

Deux paramètres régionaux sont égaux s’ils s’agit des mêmes paramètres régionaux, si l’un est une copie de l’autre, ou s’ils ont des noms identiques.

### <a name="example"></a>Exemple

```cpp
// locale_op_eq.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 == loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are not equal."
      << endl;

   if ( loc1 == loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are not equal."
      << endl;
}
```

```Output
locales loc1 (German_Germany.1252)
and loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252)
and loc3 (English_United States.1252) are not equal.
```

## <a name="see-also"></a>Voir aussi

[\<locale>](../standard-library/locale.md)<br/>
[Pages de codes](../c-runtime-library/code-pages.md)<br/>
[Chaînes relatives aux noms des paramètres régionaux, aux langues et au pays/à la région](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
