---
title: num_put, classe
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_put
- locale/std::num_put::char_type
- locale/std::num_put::iter_type
- locale/std::num_put::do_put
- locale/std::num_put::put
helpviewer_keywords:
- std::num_put [C++]
- std::num_put [C++], char_type
- std::num_put [C++], iter_type
- std::num_put [C++], do_put
- std::num_put [C++], put
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
ms.openlocfilehash: ac034a4b80225bd9674e72ca3255938316c5905a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457700"
---
# <a name="numput-class"></a>num_put, classe

Classe de modèle qui décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de valeurs numériques en séquences de type `CharType`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>Paramètres

*CharType*\
Type utilisé dans un programme pour encoder des caractères dans des paramètres régionaux spécifiques.

*OutputIterator*\
Type d'itérateur dans lequel les fonctions numériques Put écrivent leur sortie.

## <a name="remarks"></a>Notes

Comme avec n'importe quelle facette de paramètres régionaux, l'ID d'objet statique possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans **id.**

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[num_put](#num_put)|Constructeur des objets de type `num_put`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.|
|[iter_type](#iter_type)|Type qui décrit un itérateur de sortie.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[do_put](#do_put)|Fonction virtuelle qui est appelée pour convertir un nombre en une séquence de `CharType` qui représente le nombre au format de paramètres régionaux donnés.|
|[put](#put)|Convertit un nombre en une séquence de `CharType` qui représente le nombre au format de paramètres régionaux donnés.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="char_type"></a>  num_put::char_type

Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `CharType`.

## <a name="do_put"></a>  num_put::do_put

Fonction virtuelle qui est appelée pour convertir un nombre en une séquence de `CharType` qui représente le nombre au format de paramètres régionaux donnés.

```cpp
virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const long long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const unsigned long long val) const;
```

### <a name="parameters"></a>Paramètres

*Situé*\
Itérateur qui traite le premier élément de la chaîne insérée.

*_Iosbase*\
Spécifie le flux qui contient des paramètres régionaux avec la facette numpunct utilisée pour les signes de ponctuation de la sortie et des indicateurs pour la mise en forme de la sortie.

*_Fill*\
Caractère utilisé pour l’espacement.

*multiples*\
Nombre ou type booléen à envoyer en sortie.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie qui traite la position située juste au-delà du dernier élément produit.

### <a name="remarks"></a>Notes

La première fonction membre protégée virtuelle génère des éléments séquentiels en commençant à la *suite* de la génération d’un champ de sortie d’entier à partir de la valeur de *Val*. La fonction retourne un itérateur désignant l’emplacement suivant où insérer un élément au-delà du champ de sortie d’entier généré.

Le champ de sortie entier est généré par les mêmes règles que celles utilisées par les fonctions d’impression pour la génération d’une série d’éléments **char** dans un fichier. Chacun de ces éléments char est supposé être mappé à un élément équivalent de `CharType` type par un simple mappage un-à-un. Quand une fonction d’impression remplit un champ avec des espaces ou le chiffre 0, `do_put` elle utilise `fill`à la place. La spécification de conversion d’impression équivalente est déterminée comme suit :

- Si **iosbase**. [Flags](../standard-library/ios-base-class.md#flags) & Oct,`ios_base::basefield`la spécification[](../standard-library/ios-functions.md#oct)de conversion est .`lo` == `ios_base::`

- Si **iosbase. Flags** & **ios_base:: BaseField** == `ios_base::`[Hex](../standard-library/ios-functions.md#hex), la spécification de `lx`conversion est.

- Autrement, la spécification de conversion est `ld`.

Si **iosbase**. [width](../standard-library/ios-base-class.md#width) est différent de zéro, une largeur de champ de cette valeur est ajoutée. La fonction appelle ensuite **iosbase**. **width**(0) pour réinitialiser la largeur du champ à la valeur zéro.

Le remplissage se produit uniquement si le nombre minimal d’éléments *N* exigé pour spécifier le champ de sortie est inférieur à **iosbase**. [width](../standard-library/ios-base-class.md#width). Ce remplissage est constitué d’une séquence de *N* - exemplaires de**largeur** de **remplissage**. Le remplissage se produit ensuite comme suit :

- Si **iosbase**. **Flags** & `ios_base::adjustfield`Left,l' **indicateur-** est ajouté au début.[](../standard-library/ios-functions.md#left) == `ios_base::` (Le remplissage se produit après le texte généré.)

- Si **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[internal](../standard-library/ios-functions.md#internal), l’indicateur **0** est ajouté. (Pour un champ de sortie numérique, le remplissage se produit là où les fonctions d’impression remplissent avec 0.)

- Autrement, aucun indicateur supplémentaire n’est ajouté. (Le remplissage se produit avant la séquence générée.)

Pour finir :

- Si **iosbase**. **flags** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) est différent de zéro, l’indicateur **+** est ajouté à la spécification de conversion.

- Si **iosbase**. **flags** & **ios_base::** [showbase](../standard-library/ios-functions.md#showbase) est différent de zéro, l’indicateur **#** est ajouté à la spécification de conversion.

Le format d’un champ de sortie d’entier est également déterminé par la [facette de paramètres régionaux](../standard-library/locale-class.md#facet_class)**fac** retournée par l’appel [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). Plus précisément :

- **fac**. [grouping](../standard-library/numpunct-class.md#grouping) détermine comment les chiffres sont regroupés à gauche de la virgule décimale.

- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) détermine la séquence qui sépare les groupes de chiffres à gauche de la virgule décimale.

Si aucune contrainte de regroupement n’est imposée par **fac**. **grouping** (son premier élément a la valeur CHAR_MAX), aucune instance de **fac**. `thousands_sep` n’est générée dans le champ de sortie. Autrement, les séparateurs sont insérés après que la conversion d’impression a eu lieu.

La deuxième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    unsigned long val) const;
```

Se comporte comme la première, sauf qu’elle remplace une spécification de conversion de `ld` par `lu`.

La troisième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    double val) const;
```

Se comporte comme la première, sauf qu’elle génère un champ de sortie à virgule flottante à partir de la valeur de **val**. **fac**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) détermine la séquence qui sépare les chiffres entiers des chiffres de fraction. La spécification de conversion d’impression équivalente est déterminée comme suit :

- Si **iosbase**. **indicateurs** & [résolus](../standard-library/ios-functions.md#fixed), la spécification de conversion est`lf`.`ios_base::floatfield` == `ios_base::`

- Si **iosbase**. **flags** & **ios_base::floatfield** == `ios_base::`[scientific](../standard-library/ios-functions.md#scientific), la spécification de conversion est `le`. Si **iosbase**.  & la valeur[majuscule](../standard-library/ios-functions.md#uppercase) des indicateurs`ios_base::`est `e` différente de zéro `E`, est remplacée par.

- Autrement, la spécification de conversion est **lg**. Si **iosbase**. **Flags** & **ios_base:: uppercase** est différent de `g` zéro, est `G`remplacé par.

Si **iosbase**. **flags** & **ios_base::fixed** est différent de zéro ou si **iosbase**. [precision](../standard-library/ios-base-class.md#precision) est supérieure à zéro, une précision avec la valeur **iosbase**. **precision** est ajoutée à la spécification de conversion. Tout remplissage se comporte comme pour un champ de sortie d’entier. Le caractère de remplissage est **fill**. Pour finir :

- Si **iosbase**. **flags** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) est différent de zéro, l’indicateur **+** est ajouté à la spécification de conversion.

- Si **iosbase**. **flags** & `ios_base::`[showpoint](../standard-library/ios-functions.md#showpoint) est différent de zéro, l’indicateur **#** est ajouté à la spécification de conversion.

La quatrième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

se comporte de la même façon que le troisième, sauf que le `l` qualificateur dans la spécification de conversion est `L`remplacé par.

La cinquième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void* val) const;
```

Se comporte comme la première, sauf que la spécification de conversion est `p` **,** plus tout qualificateur nécessaire pour spécifier le remplissage.

La sixième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```

se comporte de la même façon que la première, sauf qu’elle génère un champ de sortie booléen à partir de *Val*.

Un champ de sortie booléen peut avoir deux formes. Si `iosbase.flags & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) a la **valeur false**, la `do_put(_Next, _Iosbase, _Fill, (long)val)`fonction membre retourne, ce qui produit généralement une séquence générée de 0 (pour **false**) ou 1 (pour **true**). Dans le cas contraire, la séquence générée est soit *FAC*. [falsename](../standard-library/numpunct-class.md#falsename) (pour **false**) ou *FAC*. [TrueName](../standard-library/numpunct-class.md#truename) (pour **true**).

La septième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    long long val) const;
```

Se comporte comme la première, sauf qu’elle remplace une spécification de conversion de `ld` par `lld`.

La huitième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    unsigned long long val) const;
```

Se comporte comme la première, sauf qu’elle remplace une spécification de conversion de `ld` par `llu`.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [put](#put), qui appelle `do_put`.

## <a name="iter_type"></a>  num_put::iter_type

Type qui décrit un itérateur de sortie.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle **OutputIterator.**

## <a name="num_put"></a>  num_put::num_put

Constructeur des objets de type `num_put`.

```cpp
explicit num_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Paramètres

*_Refs*\
Valeur entière utilisée pour spécifier le type de gestion de mémoire pour l’objet.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le paramètre *_Refs* et leur signification sont les suivantes:

- 0 : La durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : La durée de vie de l’objet doit être gérée manuellement.

- \>1: Ces valeurs ne sont pas définies.

Aucun exemple direct n’est possible, car le destructeur est protégé.

Le constructeur initialise son objet de base avec **locale::** [facet](../standard-library/locale-class.md#facet_class)(_ *Refs*).

## <a name="put"></a>  num_put::put

Convertit un nombre en une séquence `CharType`de qui représente le nombre mis en forme pour des paramètres régionaux donnés.

```cpp
iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Unsigned long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;
```

### <a name="parameters"></a>Paramètres

*dest*\
Itérateur qui traite le premier élément de la chaîne insérée.

*_Iosbase*\
Spécifie le flux qui contient des paramètres régionaux avec la facette numpunct utilisée pour les signes de ponctuation de la sortie et des indicateurs pour la mise en forme de la sortie.

*_Fill*\
Caractère utilisé pour l’espacement.

*multiples*\
Nombre ou type booléen à envoyer en sortie.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie qui traite la position située juste au-delà du dernier élément produit.

### <a name="remarks"></a>Notes

Toutes les fonctions membres retournent [do_put](#do_put)( `next`, `_Iosbase`, `_Fill`, `val`).

### <a name="example"></a>Exemples

```cpp
// num_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );
   basic_stringstream<char> psz2;
   ios_base::iostate st = 0;
   long double fVal;
   cout << "The thousands separator is: "
        << use_facet < numpunct <char> >(loc).thousands_sep( )
        << endl;

   psz2.imbue( loc );
   use_facet < num_put < char > >
      ( loc ).put(basic_ostream<char>::_Iter(psz2.rdbuf( ) ),
                    psz2, ' ', fVal=1000.67);

   if ( st & ios_base::failbit )
      cout << "num_put( ) FAILED" << endl;
   else
      cout << "num_put( ) = " << psz2.rdbuf( )->str( ) << endl;
}
```

```Output
The thousands separator is: .
num_put( ) = 1.000,67
```

## <a name="see-also"></a>Voir aussi

[\<locale>](../standard-library/locale.md)\
[facet, classe](../standard-library/locale-class.md#facet_class)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
