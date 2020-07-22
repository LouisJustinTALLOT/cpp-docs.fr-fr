---
title: locale, classe
ms.date: 07/20/2020
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
ms.openlocfilehash: d3aaedf616bf50e18e21b465727f10190fd127b2
ms.sourcegitcommit: ac5e5edd3e4f31d5dc7df48316cb7649b3f4a41f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86872385"
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

`collate`La catégorie (LC_COLLATE) comprend les facettes suivantes :

```cpp
collate<char>
collate<wchar_t>
```

`ctype`La catégorie (LC_CTYPE) comprend les facettes suivantes :

```cpp
ctype<char>
ctype<wchar_t>
codecvt<char, char, mbstate_t>
codecvt<wchar_t, char, mbstate_t>
codecvt<char16_t, char, mbstate_t>
codecvt<char32_t, char, mbstate_t>
```

`monetary`La catégorie (LC_MONETARY) comprend les facettes suivantes :

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

`numeric`La catégorie (LC_NUMERIC) comprend les facettes suivantes :

```cpp
num_get<char, istreambuf_iterator<char>>
num_get<wchar_t, istreambuf_iterator<wchar_t>>
num_put<char, ostreambuf_iterator<char>>
num_put<wchar_t, ostreambuf_iterator<wchar_t>>
numpunct<char>
numpunct<wchar_t>
```

`time`La catégorie (LC_TIME) comprend les facettes suivantes :

```cpp
time_get<char, istreambuf_iterator<char>>
time_get<wchar_t, istreambuf_iterator<wchar_t>>
time_put<char, ostreambuf_iterator<char>>
time_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

`messages`La catégorie (LC_MESSAGES) comprend les facettes suivantes :

```cpp
messages<char>
messages<wchar_t>
```

(La dernière catégorie est requise par POSIX, mais pas par la norme C.)

Certaines de ces facettes prédéfinies sont utilisées par les `iostream` classes pour contrôler la conversion des valeurs numériques en séquences de texte.

Un objet de classe locale stocke également un nom de paramètres régionaux en tant qu’objet de classe [string](../standard-library/string-typedefs.md#string). L’utilisation d’un nom de paramètres régionaux non valide pour construire une facette de paramètres régionaux ou un objet de paramètres régionaux entraîne la levée d’un objet de la classe [runtime_error](../standard-library/runtime-error-class.md). Le nom de paramètres régionaux stocké est `"*"` si l’objet de paramètres régionaux ne peut pas être certain que les paramètres régionaux de style C correspondent exactement à celui représenté par l’objet. Sinon, vous pouvez établir des paramètres régionaux correspondants dans la bibliothèque C standard, pour certains objets de paramètres régionaux `locale_object` , en appelant `setlocale(LC_ALL , locale_object.` [Name](#name) `().c_str())` .

Dans cette implémentation, vous pouvez également appeler la fonction membre statique :

```cpp
static locale empty();
```

pour construire un objet de paramètres régionaux sans facette. Il s’agit également de paramètres régionaux transparents. Si le modèle fonctionne [has_facet](../standard-library/locale-functions.md#has_facet) et [use_facet](../standard-library/locale-functions.md#use_facet) ne peut pas trouver la facette demandée dans des paramètres régionaux transparents, ils consultent d’abord les paramètres régionaux globaux, puis, s’ils sont transparents, les paramètres régionaux classiques. Vous pouvez donc écrire :

```cpp
cout.imbue(locale::empty());
```

Les insertions ultérieures à sont converties [`cout`](../standard-library/iostream.md#cout) par l’état actuel des paramètres régionaux globaux. Vous pouvez même écrire :

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

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[category](#category)|Type entier qui fournit des valeurs de masque de bits pour indiquer des familles de facettes standard.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[Mixer](#combine)|Insère une facette à partir des paramètres régionaux spécifiés dans les paramètres régionaux cibles.|
|[name](#name)|Retourne le nom des paramètres régionaux stocké.|

### <a name="static-functions"></a>Fonctions statiques

|||
|-|-|
|[Classic](#classic)|La fonction membre statique retourne un objet de paramètres régionaux qui représente les paramètres régionaux classiques du langage C.|
|[Généralités](#global)|Réinitialise les paramètres régionaux par défaut du programme.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur =](#op_eq)|Assigne des paramètres régionaux.|
|[opérateur ! =](#op_neq)|Vérifie l'inégalité de deux ensembles de paramètres régionaux.|
|[, opérateur ()](#op_call)|Compare deux objets `basic_string`.|
|[opérateur = =](#op_eq_eq)|Vérifie l'égalité de deux ensembles de paramètres régionaux.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[facet](#facet_class)|Classe qui sert de classe de base pour toutes les facettes de paramètres régionaux.|
|[`id`](#id_class)|La classe membre fournit un ID unique de facette utilisé comme index pour rechercher les facettes de paramètres régionaux.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<locale>

**Espace de noms :** std

## <a name="localecategory"></a><a name="category"></a>paramètres régionaux :: catégorie

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

Le type est un synonyme d’un type **int** qui peut représenter un groupe d’éléments distincts d’un type de masque de masque local aux paramètres régionaux de classe ou qui peut être utilisé pour représenter l’une des catégories de paramètres régionaux C correspondants. Les éléments sont :

- `collate`, correspondant à la catégorie C LC_COLLATE

- `ctype`, correspondant à la catégorie C LC_CTYPE

- `monetary`, correspondant à la catégorie C LC_MONETARY

- `numeric`, correspondant à la catégorie C LC_NUMERIC

- `time`, correspondant à la catégorie C LC_TIME

- `messages`, correspondant à la catégorie POSIX LC_MESSAGES

Deux valeurs plus utiles sont :

- `none`, qui correspond à aucune des catégories C

- `all`, qui correspond à l’Union C de toutes les catégories LC_ALL

Vous pouvez représenter un groupe arbitraire de catégories à l’aide `OR` de avec ces constantes, comme dans `monetary` &#124; `time` .

## <a name="localeclassic"></a><a name="classic"></a>paramètres régionaux :: Classic

La fonction membre statique retourne un objet de paramètres régionaux qui représente les paramètres régionaux classiques du langage C.

```cpp
static const locale& classic();
```

### <a name="return-value"></a>Valeur renvoyée

Référence aux paramètres régionaux C.

### <a name="remarks"></a>Notes

Les paramètres régionaux C classiques sont les paramètres régionaux ASCII anglais (États-Unis) dans la bibliothèque C standard. Il s’agit des paramètres régionaux utilisés implicitement dans les programmes qui ne sont pas internationalisés.

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

## <a name="localecombine"></a><a name="combine"></a>paramètres régionaux :: combiner

Insère une facette à partir des paramètres régionaux spécifiés dans les paramètres régionaux cibles.

```cpp
template <class Facet>
locale combine(const locale& source_locale) const;
```

### <a name="parameters"></a>Paramètres

*source_locale*\
Paramètres régionaux contenant la facette à insérer dans les paramètres régionaux cibles.

### <a name="return-value"></a>Valeur renvoyée

La fonction membre retourne un objet de paramètres régionaux qui remplace ou ajoute à ** \* cette** facette `Facet` indiquée dans *source_locale*.

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

## <a name="facet-class"></a><a name="facet_class"></a>facette, classe

Classe qui sert de classe de base pour toutes les facettes de paramètres régionaux.

```cpp
class facet {
protected:
    explicit facet(size_t references = 0);
    virtual ~facet();
private:
    facet(const facet&) // not defined
    void operator=(const facet&) // not defined
};
```

### <a name="remarks"></a>Notes

Vous ne pouvez pas copier ou assigner un objet de classe `facet` . Vous pouvez construire et détruire des objets dérivés de la classe `locale::facet`, mais pas des objets de la classe de base proprement dite. En général, vous construisez un objet `_Myfac` dérivé de `facet` lorsque vous construisez un `locale` , comme dans`locale loc(locale::classic(), new _Myfac);`

Dans ce cas, le constructeur de la classe de base `facet` doit avoir un argument de *référence* zéro. Lorsque l’objet n’est plus nécessaire, il est supprimé. par conséquent, vous fournissez un argument de *références* différent de zéro uniquement dans les rares cas où vous assumez la responsabilité de la durée de vie de l’objet.

## <a name="localeglobal"></a><a name="global"></a>paramètres régionaux :: global

Réinitialise les paramètres régionaux par défaut du programme. Cet appel affecte les paramètres régionaux globaux pour C et C++.

```cpp
static locale global(const locale& new_default_locale);
```

### <a name="parameters"></a>Paramètres

*new_default_locale*\
Paramètres régionaux à utiliser comme paramètres régionaux par défaut par le programme.

### <a name="return-value"></a>Valeur renvoyée

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

## <a name="id-class"></a><a name="id_class"></a>ID (classe)

La classe membre fournit un ID unique de facette utilisé comme index pour rechercher les facettes de paramètres régionaux.

```cpp
class id
{
   protected:    id();
   private:      id(const id&)
   void operator=(const id&)  // not defined
};
```

### <a name="remarks"></a>Notes

La classe membre décrit l’objet membre statique exigé par chaque facette de paramètres régionaux unique. Vous ne pouvez pas copier ou assigner un objet de classe `id` .

## <a name="localelocale"></a><a name="locale"></a>paramètres régionaux :: paramètres régionaux

Crée des paramètres régionaux, une copie de paramètres régionaux ou une copie de paramètres régionaux où une facette ou une catégorie a été remplacée par une facette, ou une catégorie provenant d'autres paramètres régionaux. Comprend également un destructeur.

```cpp
locale();

explicit locale(const char* locale_name, category new_category = all);
explicit locale(const string& locale_name);
locale(const locale& from_locale);
locale(const locale& from_locale, const locale& Other, category new_category);
locale(const locale& from_locale, const char* locale_name, category new_category);

template <class Facet>
locale(const locale& from_locale, const Facet* new_facet);

~locale();
```

### <a name="parameters"></a>Paramètres

*locale_name*\
Nom de paramètres régionaux.

*from_locale*\
Paramètres régionaux qui doivent être copiés lors de la construction des nouveaux paramètres régionaux.

*Autres*\
Paramètres régionaux à partir desquels sélectionner une catégorie.

*new_category*\
Catégorie à substituer dans les paramètres régionaux construits.

*new_facet*\
Facette à substituer dans les paramètres régionaux construits.

### <a name="remarks"></a>Notes

Le premier constructeur initialise l’objet pour qu’il corresponde aux paramètres régionaux globaux. Les deuxième et troisième constructeurs initialisent toutes les catégories de paramètres régionaux pour que le comportement soit cohérent avec le nom des paramètres régionaux *locale_name*. Les constructeurs restants copient *from_locale*, avec les exceptions notées :

`locale(const locale& from_locale, const locale& Other, category new_category);`

remplace les *autres* facettes correspondant à une catégorie c pour laquelle C & *new_category* est différent de zéro.

`locale(const locale& from_locale, const char* locale_name, category new_category);`

`locale(const locale& from_locale, const string& locale_name, category new_category);`

remplace `locale(locale_name, all)` les facettes correspondant à une catégorie *replace_category* pour laquelle `replace_category & new_category` est différent de zéro.

`template<class Facet> locale(const locale& from_locale, Facet* new_facet);`

remplace dans (ou ajoute à) *from_locale* la facette *new_facet*, si *new_facet* n’est pas un pointeur null.

Si le nom des paramètres régionaux *locale_name* est un pointeur null ou n’est pas valide, la fonction lève [runtime_error](../standard-library/runtime-error-class.md).

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

## <a name="localename"></a><a name="name"></a>paramètres régionaux :: Name

Retourne le nom des paramètres régionaux stocké.

```cpp
string name() const;
```

### <a name="return-value"></a>Valeur renvoyée

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

## <a name="localeoperator"></a><a name="op_eq"></a>locale :: Operator =

Assigne des paramètres régionaux.

```cpp
const locale& operator=(const locale& other) noexcept;
```

## <a name="localeoperator"></a><a name="op_neq"></a>locale :: Operator ! =

Vérifie l'inégalité de deux ensembles de paramètres régionaux.

```cpp
bool operator!=(const locale& right) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
L’un des paramètres régionaux dont l’inégalité doit être testée.

### <a name="return-value"></a>Valeur renvoyée

Valeur booléenne qui est **true** si les paramètres régionaux ne sont pas des copies des mêmes paramètres régionaux. La **valeur est false** si les paramètres régionaux sont des copies des mêmes paramètres régionaux.

### <a name="remarks"></a>Notes

Deux paramètres régionaux sont égaux s’ils sont identiques, s’il s’agit d’une copie de l’autre ou s’ils ont des noms identiques.

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

## <a name="localeoperator"></a><a name="op_call"></a>locale :: Operator ()

Compare deux `basic_string` objets en fonction des règles de comparaison lexicographique définies par la facette std :: COLLATE de ces paramètres régionaux <charT> .

```cpp
template <class CharType, class Traits, class Allocator>
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right) const;
```

### <a name="parameters"></a>Paramètres

*gauche*\
Première chaîne à comparer.

*Oui*\
Deuxième chaîne à comparer.

### <a name="return-value"></a>Valeur renvoyée

- `true`Si *Left* est vue lexicographique inférieur à *Right*; sinon, `false` .

### <a name="remarks"></a>Notes

La fonction de modèle exécute :

```cpp
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```

Cela signifie que vous pouvez utiliser un objet de paramètres régionaux en tant qu’objet de fonction.

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
   const wchar_t *sa = L"ztesting";
   const wchar_t *sb = L"\0x00DFtesting";
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

## <a name="localeoperator"></a><a name="op_eq_eq"></a>paramètres régionaux :: Operator = =

Vérifie l'égalité de deux ensembles de paramètres régionaux.

```cpp
bool operator==(const locale& right) const;
```

### <a name="parameters"></a>Paramètres

*Oui*\
L’un des paramètres régionaux dont l’égalité doit être testée.

### <a name="return-value"></a>Valeur renvoyée

Valeur booléenne qui est **true** si les paramètres régionaux sont des copies des mêmes paramètres régionaux. La **valeur est false** si les paramètres régionaux ne sont pas des copies des mêmes paramètres régionaux.

### <a name="remarks"></a>Notes

Deux paramètres régionaux sont égaux s’ils sont identiques, s’il s’agit d’une copie de l’autre ou s’ils ont des noms identiques.

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

[\<locale>](../standard-library/locale.md)\
[Pages de codes](../c-runtime-library/code-pages.md)\
[Chaînes de noms de paramètres régionaux, de langues et de pays/région](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
