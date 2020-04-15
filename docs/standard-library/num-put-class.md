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
ms.openlocfilehash: 3f65d7140bb5c691fa58ec9d74ceda5573280ddb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373647"
---
# <a name="num_put-class"></a>num_put, classe

Un modèle de classe qui décrit un objet qui peut servir de facette locale `CharType`pour contrôler les conversions de valeurs numériques en séquences de type .

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>Paramètres

*CharType CharType*\
Type utilisé dans un programme pour encoder des caractères dans des paramètres régionaux spécifiques.

*Iterator De sortie*\
Type d'itérateur dans lequel les fonctions numériques Put écrivent leur sortie.

## <a name="remarks"></a>Notes

Comme avec n'importe quelle facette de paramètres régionaux, l'ID d'objet statique possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans **id.**

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[num_put](#num_put)|Constructeur des objets de type `num_put`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.|
|[iter_type](#iter_type)|Type qui décrit un itérateur de sortie.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[do_put](#do_put)|Fonction virtuelle qui est appelée pour convertir un nombre en une séquence de `CharType` qui représente le nombre au format de paramètres régionaux donnés.|
|[Mettre](#put)|Convertit un nombre en une séquence de `CharType` qui représente le nombre au format de paramètres régionaux donnés.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="num_putchar_type"></a><a name="char_type"></a>num_put::char_type

Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `CharType`.

## <a name="num_putdo_put"></a><a name="do_put"></a>num_put::do-put

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

*prochain*\
Itérateur qui traite le premier élément de la chaîne insérée.

*_Iosbase*\
Spécifie le flux qui contient des paramètres régionaux avec la facette numpunct utilisée pour les signes de ponctuation de la sortie et des indicateurs pour la mise en forme de la sortie.

*_Fill*\
Caractère utilisé pour l’espacement.

*Val*\
Nombre ou type booléen à envoyer en sortie.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie qui traite la position située juste au-delà du dernier élément produit.

### <a name="remarks"></a>Notes

La première fonction virtuelle protégée des membres génère des éléments séquentiels à partir de *la suite* pour produire un champ de sortie d’intégrage à partir de la valeur de *val*. La fonction retourne un itérateur désignant l’emplacement suivant où insérer un élément au-delà du champ de sortie d’entier généré.

Le champ de sortie integer est généré par les mêmes règles utilisées par les fonctions d’impression pour générer une série d’éléments **d’omble** à un fichier. Chaque élément de char de ce genre `CharType` est supposé cartographier un élément équivalent de type par une cartographie simple et simple. Lorsqu’une fonction d’impression tampons un champ avec `do_put` des `fill`espaces ou le chiffre 0, cependant, utilise plutôt . La spécification de conversion d’impression équivalente est déterminée comme suit :

- Si **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & drapeaux ==  `lo`oct , la spécification de conversion est .[oct](../standard-library/ios-functions.md#oct)`ios_base::basefield``ios_base::`

- Si **iosbase.flags** & **ios_base::basefield** == `ios_base::`[hex](../standard-library/ios-functions.md#hex), la spécification `lx`de conversion est .

- Autrement, la spécification de conversion est `ld`.

Si **iosbase**. [width](../standard-library/ios-base-class.md#width) est différent de zéro, une largeur de champ de cette valeur est ajoutée. La fonction appelle ensuite **iosbase**. **width**(0) pour réinitialiser la largeur du champ à la valeur zéro.

Le remplissage se produit uniquement si le nombre minimal d’éléments *N* exigé pour spécifier le champ de sortie est inférieur à **iosbase**. [largeur](../standard-library/ios-base-class.md#width). Un tel rembourrage se compose d’une séquence de copies de**largeur** *N* - de **remplissage**. Le remplissage se produit ensuite comme suit :

- Si **iosbase**. **flags** & drapeaux`ios_base::adjustfield` **-** à gauche, le drapeau est prépendi.[left](../standard-library/ios-functions.md#left) == `ios_base::` (Le remplissage se produit après le texte généré.)

- Si **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[interne](../standard-library/ios-functions.md#internal), le drapeau **0** est prépendi. (Pour un champ de sortie numérique, le remplissage se produit là où les fonctions d’impression remplissent avec 0.)

- Autrement, aucun indicateur supplémentaire n’est ajouté. (Le remplissage se produit avant la séquence générée.)

Pour finir :

- Si **iosbase**. **flags** & drapeaux`ios_base::`[showpos](../standard-library/ios-functions.md#showpos) est nonzero, le drapeau **+** est prépendi à la spécification de conversion.

- Si **iosbase**. **drapeaux** & **ios_base::**[showbase](../standard-library/ios-functions.md#showbase) est nonzero, **#** le drapeau est prépendi à la spécification de conversion.

Le format d’un champ de sortie d’entier est également déterminé par la [facette de paramètres régionaux](../standard-library/locale-class.md#facet_class)**fac** retournée par l’appel [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). Plus précisément :

- **fac**. [groupement](../standard-library/numpunct-class.md#grouping) détermine comment les chiffres sont regroupés à gauche de tout point décimal

- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) détermine la séquence qui sépare les groupes de chiffres à gauche de tout point décimal

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

- Si **iosbase**. **flags** & drapeaux`ios_base::floatfield` `lf`fixes, la spécification de conversion est .[fixed](../standard-library/ios-functions.md#fixed) == `ios_base::`

- Si **iosbase**. **drapeaux** & **ios_base::floatfield** == `ios_base::`[scientifique](../standard-library/ios-functions.md#scientific), la spécification `le`de conversion est . Si **iosbase**. **flags** & drapeaux`ios_base::`[uppercase](../standard-library/ios-functions.md#uppercase) est nonzero, `e` est remplacé par `E`.

- Autrement, la spécification de conversion est **lg**. Si **iosbase**. **drapeaux** & **ios_base::uppercase** est nonzero, `g` est `G`remplacé par .

Si **iosbase**. **drapeaux** & **ios_base::fixe** est nonzero ou si **iosbase**. [precision](../standard-library/ios-base-class.md#precision) est supérieure à zéro, une précision avec la valeur **iosbase**. **precision** est ajoutée à la spécification de conversion. Tout remplissage se comporte comme pour un champ de sortie d’entier. Le caractère de remplissage est **fill**. Pour finir :

- Si **iosbase**. **flags** & drapeaux`ios_base::`[showpos](../standard-library/ios-functions.md#showpos) est nonzero, le drapeau **+** est prépendi à la spécification de conversion.

- Si **iosbase**. **flags** & drapeau`ios_base::`[showpoint](../standard-library/ios-functions.md#showpoint) est nonzero, le drapeau **#** est prépendi à la spécification de conversion.

La quatrième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

se comporte de la même façon `l` le troisième, sauf `L`que le qualificatif dans la spécification de conversion est remplacé par .

La cinquième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void* val) const;
```

Se comporte comme la première, sauf que la spécification de conversion est `p`**,** plus tout qualificateur nécessaire pour spécifier le remplissage.

La sixième fonction membre protégée virtuelle :

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```

se comporte de la même façon que le premier, sauf qu’il génère un champ de sortie Boolean à partir de *val*.

Un champ de sortie booléen peut avoir deux formes. Si `iosbase.flags & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) est **faux,** `do_put(_Next, _Iosbase, _Fill, (long)val)`la fonction membre revient , qui produit généralement une séquence générée de 0 (pour **faux**) ou 1 (pour **vrai**). Sinon, la séquence générée est soit *fac*. [falsename](../standard-library/numpunct-class.md#falsename) (pour **faux**), ou *fac*. [truename](../standard-library/numpunct-class.md#truename) (pour **vrai**).

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

## <a name="num_putiter_type"></a><a name="iter_type"></a>num_put::iter_type

Type qui décrit un itérateur de sortie.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle **OutputIterator.**

## <a name="num_putnum_put"></a><a name="num_put"></a>num_put::num_put

Constructeur des objets de type `num_put`.

```cpp
explicit num_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Paramètres

*_Refs*\
Valeur entière utilisée pour spécifier le type de gestion de mémoire pour l’objet.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le *_Refs* paramètre et leur signification sont les suivante :

- 0 : la durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : la durée de vie de l’objet doit être gérée manuellement.

- \>1: Ces valeurs ne sont pas définies.

Aucun exemple direct n’est possible, car le destructeur est protégé.

Le constructeur initialise son objet de base avec **local ::**[facette](../standard-library/locale-class.md#facet_class) *(- Refs*).

## <a name="num_putput"></a><a name="put"></a>num_put::put

Convertit un nombre en `CharType`une séquence de s qui représente le nombre formaté pour un lieu donné.

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

*Dest*\
Itérateur qui traite le premier élément de la chaîne insérée.

*_Iosbase*\
Spécifie le flux qui contient des paramètres régionaux avec la facette numpunct utilisée pour les signes de ponctuation de la sortie et des indicateurs pour la mise en forme de la sortie.

*_Fill*\
Caractère utilisé pour l’espacement.

*Val*\
Nombre ou type booléen à envoyer en sortie.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie qui traite la position située juste au-delà du dernier élément produit.

### <a name="remarks"></a>Notes

Toutes les fonctions des `next`membres `_Iosbase` `_Fill`reviennent `val` [do_put](#do_put)( , , . . . .

### <a name="example"></a>Exemple

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

[\<local>](../standard-library/locale.md)\
[Classe de facettes](../standard-library/locale-class.md#facet_class)\
[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)
