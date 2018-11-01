---
title: money_put, classe
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_put
- xlocmon/std::money_put::char_type
- xlocmon/std::money_put::iter_type
- xlocmon/std::money_put::string_type
- xlocmon/std::money_put::do_put
- xlocmon/std::money_put::put
helpviewer_keywords:
- std::money_put [C++]
- std::money_put [C++], char_type
- std::money_put [C++], iter_type
- std::money_put [C++], string_type
- std::money_put [C++], do_put
- std::money_put [C++], put
ms.assetid: f439fd56-c9b1-414c-95e1-66c918c6eee6
ms.openlocfilehash: 61f4590a7f11401601c0e11e493b49cb442cdb23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664189"
---
# <a name="moneyput-class"></a>money_put, classe

La classe de modèle décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de valeurs monétaires en séquences de type `CharType`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class money_put : public locale::facet;
```

### <a name="parameters"></a>Paramètres

*CharType*<br/>
Type utilisé dans un programme pour encoder des caractères dans des paramètres régionaux spécifiques.

*OutputIterator*<br/>
Type d'itérateur dans lequel les fonctions put monétaires enregistrent leur sortie.

## <a name="remarks"></a>Notes

Comme avec n'importe quelle facette de paramètres régionaux, l'ID d'objet statique possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans **id.**

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[money_put](#money_put)|Constructeur des objets de type `money_put`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.|
|[iter_type](#iter_type)|Type qui décrit un itérateur de sortie.|
|[string_type](#string_type)|Type qui décrit une chaîne contenant des caractères de type `CharType`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[do_put](#do_put)|Fonction virtuelle appelée pour convertir un nombre ou une chaîne en une séquence de caractères représentant une valeur monétaire.|
|[put](#put)|Convertit un nombre ou une chaîne en une séquence de caractères représentant une valeur monétaire.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="char_type"></a>  money_put::char_type

Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle **CharType**.

## <a name="do_put"></a>  money_put::do_put

Fonction virtuelle appelée pour convertir un nombre ou une chaîne en une séquence de caractères représentant une valeur monétaire.

```cpp
virtual iter_type do_put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    const string_type& val) const;

virtual iter_type do_put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

### <a name="parameters"></a>Paramètres

*next*<br/>
Itérateur qui traite le premier élément de la chaîne insérée.

*_Intl*<br/>
Valeur booléenne indiquant le type de symbole monétaire attendu dans la séquence : **true** si international, **false** si national.

*_Iosbase*<br/>
Indicateur de format qui, quand il est défini, indique que le symbole monétaire est facultatif. Dans le cas contraire, il est obligatoire.

*_Fill*<br/>
Caractère utilisé pour l’espacement.

*Val*<br/>
Objet de chaîne à convertir.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie qui traite la position située juste au-delà du dernier élément produit.

### <a name="remarks"></a>Notes

La première fonction membre protégée virtuelle génère des éléments séquentiels en commençant à *suivant* pour produire un champ de sortie monétaire à partir de la [string_type](#string_type) objet *val*. La séquence contrôlée par *val* doit commencer par un ou plusieurs chiffres décimaux, éventuellement précédés par un signe moins (-), qui représente la quantité. La fonction retourne un itérateur désignant le premier élément au-delà du champ de sortie monétaire généré.

La deuxième fonction membre protégée virtuelle comporte comme la première, sauf qu’elle convertit d’abord *val* à une séquence de chiffres décimaux, éventuellement précédé par un signe moins, puis convertit cette séquence comme ci-dessus.

Le format d’un champ de sortie monétaire est déterminé par la [facette de paramètres régionaux](../standard-library/locale-class.md#facet_class) fac retournée par l’appel (effectif) [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, **intl**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)).

Plus précisément :

- **fac**. [pos_format](../standard-library/moneypunct-class.md#pos_format) détermine l’ordre dans lequel les composants du champ sont générés pour une valeur non négative.

- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) détermine l’ordre dans lequel les composants du champ sont générés pour une valeur négative.

- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) détermine la séquence d’éléments à générer pour un symbole monétaire.

- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) détermine la séquence d’éléments à générer pour un signe positif.

- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) détermine la séquence d’éléments à générer pour un signe négatif.

- **fac**. [grouping](../standard-library/moneypunct-class.md#grouping) détermine comment les chiffres sont regroupés à gauche de la virgule décimale.

- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) détermine l’élément qui sépare les groupes de chiffres à gauche de la virgule décimale.

- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) détermine l’élément qui sépare les chiffres entiers des chiffres de fraction.

- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) détermine le nombre de chiffres de fraction significatifs à droite de la virgule décimale.

Si la chaîne de signe ( **fac**. `negative_sign` ou **fac**. `positive_sign`) comporte plusieurs éléments, seul le premier élément est généré là où l’élément égal à **money_base::sign** apparaît dans le modèle de format ( **fac**. `neg_format` ou **fac**. `pos_format`). Les éléments restants sont générés à la fin du champ de sortie monétaire.

Si **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) est différent de zéro, la chaîne **fac**. `curr_symbol` est générée là où l’élément égal à **money_base::symbol** apparaît dans le modèle de format. Sinon, aucun symbole monétaire n’est généré.

Si aucune contrainte de regroupement n’est imposée par **fac**. **grouping** (son premier élément a la valeur CHAR_MAX), aucune instance de **fac**. `thousands_sep` n’est générée dans la partie valeur du champ de sortie monétaire (où l’élément égal à **money_base::value** apparaît dans le modèle de format). If **fac**. `frac_digits` a la valeur zéro, aucune instance de **fac**. `decimal_point` n’est générée après les chiffres décimaux. Dans le cas contraire, le champ de sortie monétaire résultant place les chiffres décimaux **fac**. `frac_digits` de poids faible à droite de la virgule décimale.

Le remplissage se produit comme pour n’importe quel champ de sortie numérique, sauf que si **iosbase**. **flags** & **iosbase**. [internal](../standard-library/ios-functions.md#internal) est différent de zéro, tout remplissage interne est généré là où l’élément égal à **money_base::space** apparaît dans le modèle de format, s’il apparaît. Sinon, le remplissage interne se produit avant la séquence générée. Le caractère de remplissage est **fill**.

La fonction appelle **iosbase**. **width**(0) pour réinitialiser la largeur du champ à la valeur zéro.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [put](#put), où la fonction membre virtuelle est appelée par **put**.

## <a name="iter_type"></a>  money_put::iter_type

Type qui décrit un itérateur de sortie.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle **OutputIterator.**

## <a name="money_put"></a>  money_put::money_put

Constructeur des objets de type `money_put`.

```cpp
explicit money_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Paramètres

*_Refs*<br/>
Valeur entière utilisée pour spécifier le type de gestion de mémoire pour l’objet.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le *_Refs* paramètre et leur signification sont :

- 0 : la durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : la durée de vie de l’objet doit être gérée manuellement.

- \> 1 : ces valeurs ne sont pas définies.

Aucun exemple direct n’est possible, car le destructeur est protégé.

Le constructeur initialise son objet de base avec **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="put"></a>  money_put::put

Convertit un nombre ou une chaîne en une séquence de caractères représentant une valeur monétaire.

```cpp
iter_type put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    const string_type& val) const;

iter_type put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

### <a name="parameters"></a>Paramètres

*next*<br/>
Itérateur qui traite le premier élément de la chaîne insérée.

*_Intl*<br/>
Valeur booléenne indiquant le type de symbole monétaire attendu dans la séquence : **true** si international, **false** si national.

*_Iosbase*<br/>
Indicateur de format qui, quand il est défini, indique que le symbole monétaire est facultatif. Dans le cas contraire, il est obligatoire.

*_Fill*<br/>
Caractère utilisé pour l’espacement.

*Val*<br/>
Objet de chaîne à convertir.

### <a name="return-value"></a>Valeur de retour

Itérateur de sortie qui traite la position située juste au-delà du dernier élément produit.

### <a name="remarks"></a>Notes

Les deux fonctions membres retournent [do_put](#do_put)( `next`, `_Intl`, `_Iosbase`, `_Fill`, `val`).

### <a name="example"></a>Exemple

```cpp
// money_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
//   locale loc( "german_germany" );
   locale loc( "english_canada" );
   basic_stringstream<char> psz, psz2;
   ios_base::iostate st = 0;

   psz2.imbue( loc );
   psz2.flags( psz2.flags( )|ios_base::showbase ); // force the printing of the currency symbol
   use_facet < money_put < char > >(loc).put(basic_ostream<char>::_Iter( psz2.rdbuf( ) ), true, psz2, st, 100012);
   if (st & ios_base::failbit)
      cout << "money_put( ) FAILED" << endl;
   else
      cout << "money_put( ) = \"" << psz2.rdbuf( )->str( ) <<"\""<< endl;

   st = 0;
};
```

```Output
money_put( ) = "CAD1,000.12"
```

## <a name="string_type"></a>  money_put::string_type

Type qui décrit une chaîne contenant des caractères de type `CharType`.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation de la classe de modèle [basic_string](../standard-library/basic-string-class.md) dont les objets peuvent stocker des séquences d’éléments à partir de la séquence source.

## <a name="see-also"></a>Voir aussi

[\<locale>](../standard-library/locale.md)<br/>
[Facet, classe](../standard-library/locale-class.md#facet_class)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
