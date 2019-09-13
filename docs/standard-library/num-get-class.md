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
ms.openlocfilehash: 67aef1ce52b6717ce6d6381429982cf660aa5e20
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457640"
---
# <a name="num_get-class"></a>num_get, classe

Classe de modèle qui décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de séquences de type `CharType` en valeurs numériques.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>Paramètres

*CharType*\
Type utilisé dans un programme pour encoder des caractères dans des paramètres régionaux spécifiques.

*InputIterator*\
Type d'itérateur depuis lequel les fonctions get numériques lisent leur entrée.

## <a name="remarks"></a>Notes

Comme avec n'importe quelle facette de paramètres régionaux, l'ID d'objet statique possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans **id.**

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[num_get](#num_get)|Constructeur des objets de type `num_get` utilisés pour extraire des valeurs numériques depuis des séquences.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.|
|[iter_type](#iter_type)|Type qui décrit un itérateur d'entrée.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[do_get](#do_get)|Fonction virtuelle appelée pour extraire une valeur numérique ou booléenne depuis une séquence de caractères.|
|[get](#get)|Extrait une valeur numérique ou booléenne d'une séquence de caractères.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="char_type"></a>  num_get::char_type

Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle **CharType**.

## <a name="do_get"></a>  num_get::do_get

Fonction virtuelle appelée pour extraire une valeur numérique ou booléenne depuis une séquence de caractères.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Début de la plage de caractères à partir de laquelle lire le nombre.

*famille*\
Fin de la plage de caractères à partir de laquelle lire le nombre.

*_Iosbase*\
[ios_base](../standard-library/ios-base-class.md) dont les indicateurs sont utilisés par la conversion.

*_ State*\
État auquel failbit (voir [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) est ajouté en cas d’échec.

*multiples*\
Valeur qui a été lue.

### <a name="return-value"></a>Valeur de retour

Itérateur une fois que la valeur a été lue.

### <a name="remarks"></a>Notes

La première fonction membre protégée virtuelle,

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;
```

met en correspondance les éléments séquentiels en commençant `[first, last)` au premier dans la séquence jusqu’à ce qu’il ait reconnu un champ d’entrée d’entier non vide complet. En cas de réussite, elle convertit ce champ en sa valeur équivalente en tant que type **long**et stocke le résultat dans *Val*. Elle retourne un itérateur désignant le premier élément au-delà du champ d’entrée numérique. Sinon, la fonction ne stocke rien dans Val `ios_base::failbit` et `state`définit dans. Elle retourne un itérateur désignant le premier élément au-delà de tout préfixe d’un champ d’entrée d’entier valide. Dans les deux cas, si la valeur de retour est égale à `last`, la fonction définit `ios_base::eofbit` dans `state`.

Le champ d’entrée d’entier est converti par les mêmes règles que celles utilisées par les fonctions d’analyse pour la correspondance et la conversion d’une série d’éléments **char** à partir d’un fichier. (Chaque élément de type **char** est supposé être mappé à un élément équivalent de `Elem` type par un mappage simple, un-à-un.) La spécification de conversion d’analyse équivalente est déterminée comme suit :

Si `iosbase.`[ios_base::flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct), la spécification de conversion est `lo`.

Si `iosbase.flags() & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex), la spécification de conversion est `lx`.

Si `iosbase.flags() & ios_base::basefield == 0`, la spécification de conversion est `li`.

Autrement, la spécification de conversion est `ld`.

Le format d’un champ d’entrée d’entier est également déterminé par la [facette de paramètres régionaux](../standard-library/locale-class.md#facet_class)`fac` retournée par l’appel [use_facet](../standard-library/locale-functions.md#use_facet) `<`[numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.` [ios_base::getloc](../standard-library/ios-base-class.md#getloc)`())`. Plus précisément :

`fac.` [numpunct::grouping](../standard-library/numpunct-class.md#grouping) `()` détermine comment les chiffres sont regroupés à gauche de la virgule décimale.

`fac.` [numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` détermine la séquence qui sépare les groupes de chiffres à gauche de la virgule décimale.

Si aucune instance de `fac.thousands_sep()` ne se produit dans le champ d’entrée numérique, aucune contrainte de regroupement n’est imposée. Autrement, toute contrainte de regroupement imposée par `fac.grouping()` est appliquée, et les séparateurs sont supprimés avant que la conversion d’analyse ait lieu.

La quatrième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```

Se comporte comme la première, sauf qu’elle remplace une spécification de conversion de `ld` par `lu`. En cas de réussite, elle convertit le champ d’entrée numérique en une valeur de type **unsigned long** et stocke cette valeur dans *Val*.

La cinquième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;
```

Se comporte comme la première, sauf qu’elle remplace une spécification de conversion de `ld` par `lld`. En cas de réussite, elle convertit le champ d’entrée numérique en une valeur de type **long long** et stocke cette valeur dans *Val*.

La sixième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;
```

Se comporte comme la première, sauf qu’elle remplace une spécification de conversion de `ld` par `llu`. En cas de réussite, elle convertit le champ d’entrée numérique en une valeur de type **unsigned long long** et stocke cette valeur dans *Val*.

La septième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;
```

Se comporte comme la première, sauf qu’elle essaie de mettre en correspondance un champ d’entrée à virgule flottante complet et non vide. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point)`()` détermine la séquence qui sépare les chiffres entiers des chiffres de fraction. Le spécificateur de conversion d’analyse équivalent est `lf`.

La huitième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```

Se comporte comme la première, sauf qu’elle essaie de mettre en correspondance un champ d’entrée à virgule flottante complet et non vide. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point)`()` détermine la séquence qui sépare les chiffres entiers des chiffres de fraction. Le spécificateur de conversion d’analyse équivalent est `lf`.

La neuvième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```

Se comporte comme la huitième, sauf que le spécificateur de conversion d’analyse équivalent est `Lf`.

Dixième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

Se comporte comme la première, sauf que le spécificateur de conversion d’analyse équivalent est `p`.

La dernière (onzième) fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

Se comporte comme la première, sauf qu’elle essaie de mettre en correspondance un champ d’entrée booléen complet et non vide. En cas de réussite, elle convertit le champ d’entrée booléen en valeur de type **bool** et stocke cette valeur dans *Val*.

Un champ d’entrée booléen peut avoir deux formes. Si `iosbase.flags() & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) est false, il est identique à un champ d’entrée d’entier, sauf que la valeur convertie doit être 0 (pour false) ou 1 (pour true). Dans le cas contraire, la séquence doit correspondre à `fac.`[numpunct::falsename](../standard-library/numpunct-class.md#falsename)`()` (pour false) ou à `fac.`[numpunct::truename](../standard-library/numpunct-class.md#truename)`()` (pour true).

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [get](#get), où la fonction membre virtuelle est appelée par `do_get`.

## <a name="get"></a>  num_get::get

Extrait une valeur numérique ou booléenne d'une séquence de caractères.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Début de la plage de caractères à partir de laquelle lire le nombre.

*famille*\
Fin de la plage de caractères à partir de laquelle lire le nombre.

*_Iosbase*\
[ios_base](../standard-library/ios-base-class.md) dont les indicateurs sont utilisés par la conversion.

*_ State*\
État auquel failbit (voir [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) est ajouté en cas d’échec.

*multiples*\
Valeur qui a été lue.

### <a name="return-value"></a>Valeur de retour

Itérateur une fois que la valeur a été lue.

### <a name="remarks"></a>Notes

Toutes les fonctions membres retournent [do_get](#do_get)( `first`, `last`, `_Iosbase`, `_State`, `val`).

La première fonction membre protégée virtuelle tente de faire correspondre des éléments séquentiels en commençant au premier dans la séquence [ `first`, `last`) jusqu’à ce qu’elle ait reconnu un champ d’entrée d’entier complet et non vide. En cas de réussite, elle convertit ce champ en sa valeur équivalente en tant que type **long** et stocke le résultat dans *Val*. Elle retourne un itérateur désignant le premier élément au-delà du champ d’entrée numérique. Sinon, la fonction ne stocke rien dans Val `ios_base::failbit` et définit dans l' *État*_. Elle retourne un itérateur désignant le premier élément au-delà de tout préfixe d’un champ d’entrée d’entier valide. Dans les deux cas, si la valeur de retour est égale à *Last*, `ios_base::eofbit` la fonction définit dans _ *State*.

Le champ d’entrée d’entier est converti par les mêmes règles que celles utilisées par les fonctions d’analyse pour la correspondance et la conversion d’une série d’éléments **char** à partir d’un fichier. Chacun de ces éléments **char** est supposé être mappé à un élément équivalent de `CharType` type par un simple mappage un-à-un. La spécification de conversion d’analyse équivalente est déterminée comme suit :

- Si `iosbase`. [Flags](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[Oct](../standard-library/ios-functions.md#oct),la spécification de conversion est `lo`.

- Si **iosbase. Flags** & **ios_base :: BaseField** == `ios_base::`[Hex](../standard-library/ios-functions.md#hex), la spécification de `lx`conversion est.

- Si **iosbase.flags** & **ios_base::basefield** == 0, la spécification de conversion est `li`.

- Autrement, la spécification de conversion est `ld`.

Le format d’un champ d’entrée d’entier est également déterminé par la [facette de paramètres régionaux](../standard-library/locale-class.md#facet_class)**fac** retournée par l’appel [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). Plus précisément :

- **fac**. [grouping](../standard-library/numpunct-class.md#grouping) détermine comment les chiffres sont regroupés à gauche de la virgule décimale.

- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) détermine la séquence qui sépare les groupes de chiffres à gauche de la virgule décimale.

Si aucune instance de **fac**. `thousands_sep` ne se produit dans le champ d’entrée numérique, aucune contrainte de regroupement n’est imposée. Autrement, toute contrainte de regroupement imposée par **fac**. **grouping** est appliquée, et les séparateurs sont supprimés avant que la conversion d’analyse ait lieu.

La deuxième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```

Se comporte comme la première, sauf qu’elle remplace une spécification de conversion de `ld` par `lu`. En cas de réussite, elle convertit le champ d’entrée numérique en une valeur de type **unsigned long** et stocke cette valeur dans *Val*.

La troisième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```

Se comporte comme la première, sauf qu’elle essaie de mettre en correspondance un champ d’entrée à virgule flottante complet et non vide. **fac**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) détermine la séquence qui sépare les chiffres entiers des chiffres de fraction. Le spécificateur de conversion d’analyse équivalent est `lf`.

La quatrième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```

se comporte de la même façon que le troisième, sauf que le spécificateur de conversion d' `Lf`analyse équivalent est.

La cinquième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

Se comporte comme la première, sauf que le spécificateur de conversion d’analyse équivalent est `p`.

La sixième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

Se comporte comme la première, sauf qu’elle essaie de mettre en correspondance un champ d’entrée booléen complet et non vide. En cas de réussite, elle convertit le champ d’entrée booléen en valeur de type **bool** et stocke cette valeur dans *Val*.

Un champ d’entrée booléen peut avoir deux formes. Si **iosbase**. **flags** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) est **false**, il est identique à un champ d’entrée d’entier, sauf que la valeur convertie doit être 0 (pour **false**) ou 1 (pour **true**). Autrement, la séquence doit correspondre à **fac**. [falsename](../standard-library/numpunct-class.md#falsename) (pour **false**) ou à **fac**. [truename](../standard-library/numpunct-class.md#truename) (pour **true**).

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

## <a name="iter_type"></a>  num_get::iter_type

Type qui décrit un itérateur d'entrée.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `InputIterator`.

## <a name="num_get"></a>  num_get::num_get

Constructeur des objets de type `num_get` utilisés pour extraire des valeurs numériques depuis des séquences.

```cpp
explicit num_get(size_t _Refs = 0);
```

### <a name="parameters"></a>Paramètres

*_Refs*\
Valeur entière utilisée pour spécifier le type de gestion de mémoire pour l’objet.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le paramètre *_Refs* et leur signification sont les suivantes :

- 0 : La durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : La durée de vie de l’objet doit être gérée manuellement.

- \>1 : Ces valeurs ne sont pas définies.

Aucun exemple direct n’est possible, car le destructeur est protégé.

Le constructeur initialise son objet de base avec **locale::** [facet](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="see-also"></a>Voir aussi

[\<locale>](../standard-library/locale.md)\
[facet, classe](../standard-library/locale-class.md#facet_class)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
