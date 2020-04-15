---
title: num_get, classe
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
helpviewer_keywords:
- std::num_get [C++]
- std::num_get [C++], char_type
- std::num_get [C++], iter_type
- std::num_get [C++], do_get
- std::num_get [C++], get
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
ms.openlocfilehash: 76d2832141c65ca67c42f1994a3c8f5b532f0092
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373658"
---
# <a name="num_get-class"></a>num_get, classe

Un modèle de classe qui décrit un objet qui peut servir de facette locale pour contrôler les conversions de séquences de type `CharType` à des valeurs numériques.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>Paramètres

*CharType CharType*\
Type utilisé dans un programme pour encoder des caractères dans des paramètres régionaux spécifiques.

*InputIterator (en)*\
Type d'itérateur depuis lequel les fonctions get numériques lisent leur entrée.

## <a name="remarks"></a>Notes

Comme avec n'importe quelle facette de paramètres régionaux, l'ID d'objet statique possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans **id.**

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[num_get](#num_get)|Constructeur des objets de type `num_get` utilisés pour extraire des valeurs numériques depuis des séquences.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.|
|[iter_type](#iter_type)|Type qui décrit un itérateur d'entrée.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[do_get](#do_get)|Fonction virtuelle appelée pour extraire une valeur numérique ou booléenne depuis une séquence de caractères.|
|[get](#get)|Extrait une valeur numérique ou booléenne d'une séquence de caractères.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="num_getchar_type"></a><a name="char_type"></a>num_get::char_type

Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle **CharType**.

## <a name="num_getdo_get"></a><a name="do_get"></a>num_get: :do-get

Fonction virtuelle appelée pour extraire une valeur numérique ou booléenne depuis une séquence de caractères.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

### <a name="parameters"></a>Paramètres

*Première*\
Début de la plage de caractères à partir de laquelle lire le nombre.

*Dernière*\
Fin de la plage de caractères à partir de laquelle lire le nombre.

*iosbase*\
[ios_base](../standard-library/ios-base-class.md) dont les indicateurs sont utilisés par la conversion.

*État*\
État auquel failbit (voir [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) est ajouté en cas d’échec.

*Val*\
Valeur qui a été lue.

### <a name="return-value"></a>Valeur de retour

Itérateur une fois que la valeur a été lue.

### <a name="remarks"></a>Notes

La première fonction membre protégée virtuelle,

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;
```

correspond à des éléments séquentiels à partir du *début* de la séquence `[first, last)` jusqu’à ce qu’il ait reconnu un champ d’entrée complet et non rédempteur. En cas de succès, il convertit ce champ à sa valeur équivalente comme type **long,** et stocke le résultat en *val*. Elle retourne un itérateur désignant le premier élément au-delà du champ d’entrée numérique. Sinon, la fonction ne stocke `state`rien dans *val* et s’installe `ios_base::failbit` . Elle retourne un itérateur désignant le premier élément au-delà de tout préfixe d’un champ d’entrée d’entier valide. Dans les deux cas, si la valeur de retour est égale à `last`, la fonction définit `ios_base::eofbit` dans `state`.

Le champ d’entrée integer est converti par les mêmes règles utilisées par les fonctions d’analyse pour l’appariement et la conversion d’une série d’éléments **d’omble d’un** fichier. (Chaque élément **de char** de ce genre `Elem` est supposé cartographier un élément équivalent de type par une cartographie simple et simple.) La spécification de conversion d’analyse équivalente est déterminée comme suit :

Si `iosbase.` [ios_base::flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct), la spécification `lo`de conversion est .

Si `iosbase.flags() & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex), la spécification de conversion est `lx`.

Si `iosbase.flags() & ios_base::basefield == 0`, la spécification de conversion est `li`.

Autrement, la spécification de conversion est `ld`.

Le format d’un champ d’entrée integer est encore déterminé par la [facette](../standard-library/locale-class.md#facet_class) `fac` locale retournée par l’appel [use_facet](../standard-library/locale-functions.md#use_facet) `<` [numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.`[ios_base::getloc](../standard-library/ios-base-class.md#getloc)`())`. Plus précisément :

`fac.`[numpunct::groupement](../standard-library/numpunct-class.md#grouping) `()` détermine comment les chiffres sont regroupés à gauche de tout point décimal

`fac.`[numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` détermine la séquence qui sépare les groupes de chiffres à gauche de tout point décimal.

Si aucune instance de `fac.thousands_sep()` ne se produit dans le champ d’entrée numérique, aucune contrainte de regroupement n’est imposée. Autrement, toute contrainte de regroupement imposée par `fac.grouping()` est appliquée, et les séparateurs sont supprimés avant que la conversion d’analyse ait lieu.

La quatrième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

Se comporte comme la première, sauf qu’elle remplace une spécification de conversion de `ld` par `lu`. En cas de succès, il convertit le champ d’entrée numérique en une valeur de type **non signé long** et stocke cette valeur en *val*.

La cinquième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;
```

Se comporte comme la première, sauf qu’elle remplace une spécification de conversion de `ld` par `lld`. En cas de succès, il convertit le champ d’entrée numérique à une valeur de type **long** et stocke cette valeur en *val*.

La sixième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;
```

Se comporte comme la première, sauf qu’elle remplace une spécification de conversion de `ld` par `llu`. En cas de succès, il convertit le champ d’entrée numérique à une valeur de type **non signé longtemps** et stocke cette valeur en *val*.

La septième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;
```

Se comporte comme la première, sauf qu’elle essaie de mettre en correspondance un champ d’entrée à virgule flottante complet et non vide. `fac.`[numpunct::decimal-point](../standard-library/numpunct-class.md#decimal_point) `()` détermine la séquence qui sépare les chiffres integer des chiffres fraction. Le spécificateur de conversion d’analyse équivalent est `lf`.

La huitième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

Se comporte comme la première, sauf qu’elle essaie de mettre en correspondance un champ d’entrée à virgule flottante complet et non vide. `fac.`[numpunct::decimal-point](../standard-library/numpunct-class.md#decimal_point) `()` détermine la séquence qui sépare les chiffres integer des chiffres fraction. Le spécificateur de conversion d’analyse équivalent est `lf`.

La neuvième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

Se comporte comme la huitième, sauf que le spécificateur de conversion d’analyse équivalent est `Lf`.

La dixième fonction virtuelle protégée des membres :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

Se comporte comme la première, sauf que le spécificateur de conversion d’analyse équivalent est `p`.

La dernière (onzième) fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

Se comporte comme la première, sauf qu’elle essaie de mettre en correspondance un champ d’entrée booléen complet et non vide. En cas de succès, il convertit le champ d’entrée Boolean en une valeur de type **bool** et stocke cette valeur en *val*.

Un champ d’entrée booléen peut avoir deux formes. Si `iosbase.flags() & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) est false, il est identique à un champ d’entrée d’entier, sauf que la valeur convertie doit être 0 (pour false) ou 1 (pour true). Sinon, la séquence `fac.`doit correspondre soit [numpunct::falsename](../standard-library/numpunct-class.md#falsename) `()` (pour faux), ou `fac.` [numpunct::truename](../standard-library/numpunct-class.md#truename) `()` (pour vrai).

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [get](#get), où la fonction membre virtuelle est appelée par `do_get`.

## <a name="num_getget"></a><a name="get"></a>num_get::get

Extrait une valeur numérique ou booléenne d'une séquence de caractères.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

### <a name="parameters"></a>Paramètres

*Première*\
Début de la plage de caractères à partir de laquelle lire le nombre.

*Dernière*\
Fin de la plage de caractères à partir de laquelle lire le nombre.

*iosbase*\
[ios_base](../standard-library/ios-base-class.md) dont les indicateurs sont utilisés par la conversion.

*État*\
État auquel failbit (voir [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) est ajouté en cas d’échec.

*Val*\
Valeur qui a été lue.

### <a name="return-value"></a>Valeur de retour

Itérateur une fois que la valeur a été lue.

### <a name="remarks"></a>Notes

Toutes les fonctions des membres reviennent [do_get](#do_get)`( first, last, iosbase, state, val)`.

La première fonction membre protégée virtuelle tente de faire correspondre des éléments séquentiels en commençant au premier dans la séquence [ `first`, `last`) jusqu’à ce qu’elle ait reconnu un champ d’entrée d’entier complet et non vide. En cas de succès, il convertit ce champ à sa valeur équivalente en tant que type **long** et stocke le résultat en *val*. Elle retourne un itérateur désignant le premier élément au-delà du champ d’entrée numérique. Sinon, la fonction ne stocke rien dans *val* et s’installe `ios_base::failbit` en *état*. Elle retourne un itérateur désignant le premier élément au-delà de tout préfixe d’un champ d’entrée d’entier valide. Dans les deux cas, si la valeur `ios_base::eofbit` de rendement est égale en *dernier*, la fonction *s’établit*en état .

Le champ d’entrée integer est converti par les mêmes règles utilisées par les fonctions d’analyse pour l’appariement et la conversion d’une série d’éléments **d’omble d’un** fichier. Chaque élément **de char** de ce genre `CharType` est supposé cartographier un élément équivalent de type par une cartographie simple et simple. La spécification de conversion d’analyse équivalente est déterminée comme suit :

- Si `iosbase.` [les drapeaux](../standard-library/ios-base-class.md#flags)`& ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct), `lo`la spécification de conversion est .

- Si `iosbase.flags & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex), la spécification de conversion est `lx`.

- Si `iosbase.flags & ios_base::basefield == 0`, la spécification de conversion est `li`.

- Autrement, la spécification de conversion est `ld`.

Le format d’un champ d’entrée integer est encore déterminé par la [facette](../standard-library/locale-class.md#facet_class) `fac` locale retournée par l’appel [use_facet](../standard-library/locale-functions.md#use_facet)`<`[`numpunct`](../standard-library/numpunct-class.md)`<Elem>(iosbase.`[getloc](../standard-library/ios-base-class.md#getloc)`())`. Plus précisément :

- `fac.`[le regroupement](../standard-library/numpunct-class.md#grouping) détermine comment les chiffres sont regroupés à gauche de n’importe quel point décimal.

- `fac.`[thousands_sep](../standard-library/numpunct-class.md#thousands_sep) détermine la séquence qui sépare les groupes de chiffres à gauche de tout point décimal.

Si aucune instance de `fac.thousands_sep` ne se produit dans le champ d’entrée numérique, aucune contrainte de regroupement n’est imposée. Dans le cas contraire, `fac.grouping` toutes les contraintes de regroupement imposées par est appliquée et les séparateurs sont supprimés avant la conversion de balayage se produit.

La deuxième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

Se comporte comme la première, sauf qu’elle remplace une spécification de conversion de `ld` par `lu`. En cas de succès, il convertit le champ d’entrée numérique en une valeur de type **non signé long** et stocke cette valeur en *val*.

La troisième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

Se comporte comme la première, sauf qu’elle essaie de mettre en correspondance un champ d’entrée à virgule flottante complet et non vide. `fac.`[decimal_point](../standard-library/numpunct-class.md#decimal_point) détermine la séquence qui sépare les chiffres de l’intégrant des chiffres fractionnés. Le spécificateur de conversion d’analyse équivalent est `lf`.

La quatrième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

se comporte de la même façon le troisième, `Lf`sauf que le spécificateur de conversion d’analyse équivalent est .

La cinquième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

Se comporte comme la première, sauf que le spécificateur de conversion d’analyse équivalent est `p`.

La sixième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

Se comporte comme la première, sauf qu’elle essaie de mettre en correspondance un champ d’entrée booléen complet et non vide. En cas de succès, il convertit le champ d’entrée Boolean en une valeur de type **bool** et stocke cette valeur en *val*.

Un champ d’entrée booléen peut avoir deux formes. Si `iosbase.flags & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) est **faux,** il est le même qu’un champ d’entrée integer, sauf que la valeur convertie doit être soit 0 (pour **faux**) ou 1 (pour **vrai**). Sinon, la séquence `fac.`doit correspondre soit faux `fac.` [nom](../standard-library/numpunct-class.md#falsename) (pour **faux**), ou [truename](../standard-library/numpunct-class.md#truename) (pour **vrai**).

### <a name="example"></a>Exemple

```cpp
// num_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   basic_stringstream<char> psz, psz2;
   psz << "-1000,56";

   ios_base::iostate st = 0;
   long double fVal;
   cout << use_facet <numpunct <char> >(loc).thousands_sep( ) << endl;

   psz.imbue( loc );
   use_facet <num_get <char> >
   (loc).get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter(0), psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get( ) FAILED" << endl;
   else
      cout << "money_get( ) = " << fVal << endl;
}
```

## <a name="num_getiter_type"></a><a name="iter_type"></a>num_get::iter_type

Type qui décrit un itérateur d'entrée.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `InputIterator`.

## <a name="num_getnum_get"></a><a name="num_get"></a>num_get::num_get

Constructeur des objets de type `num_get` utilisés pour extraire des valeurs numériques depuis des séquences.

```cpp
explicit num_get(size_t refs = 0);
```

### <a name="parameters"></a>Paramètres

*Refs*\
Valeur entière utilisée pour spécifier le type de gestion de mémoire pour l’objet.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le *paramètre des arbitres* et leur signification sont les suivante :

- 0 : la durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : la durée de vie de l’objet doit être gérée manuellement.

- \>1: Ces valeurs ne sont pas définies.

Aucun exemple direct n’est possible, car le destructeur est protégé.

Le constructeur initialise son objet `locale::`de base avec [la facette.](../standard-library/locale-class.md#facet_class)`(refs)`

## <a name="see-also"></a>Voir aussi

[\<local>](../standard-library/locale.md)\
[Classe de facettes](../standard-library/locale-class.md#facet_class)\
[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)
