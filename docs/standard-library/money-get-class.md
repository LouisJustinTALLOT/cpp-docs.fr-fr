---
title: money_get, classe
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_get
- xlocmon/std::money_get::char_type
- xlocmon/std::money_get::iter_type
- xlocmon/std::money_get::string_type
- xlocmon/std::money_get::do_get
- xlocmon/std::money_get::get
helpviewer_keywords:
- std::money_get [C++]
- std::money_get [C++], char_type
- std::money_get [C++], iter_type
- std::money_get [C++], string_type
- std::money_get [C++], do_get
- std::money_get [C++], get
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
ms.openlocfilehash: d882edd5ce55b15d03512ca9a55a49bc3424ee7a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687669"
---
# <a name="money_get-class"></a>money_get, classe

Le modèle de classe décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de séquences de type `CharType` en valeurs monétaires.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>Paramètres

*CharType* \
Type utilisé dans un programme pour encoder des caractères dans des paramètres régionaux spécifiques.

*InputIterator* \
Type d'itérateur depuis lequel les fonctions get lisent leur entrée.

## <a name="remarks"></a>Notes

Comme avec n'importe quelle facette de paramètres régionaux, l'ID d'objet statique possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans **id.**

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[money_get](#money_get)|Constructeur des objets de type `money_get` utilisés pour extraire des valeurs numériques de séquences représentant des valeurs monétaires.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.|
|[iter_type](#iter_type)|Type qui décrit un itérateur d'entrée.|
|[string_type](#string_type)|Type qui décrit une chaîne contenant des caractères de type `CharType`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[do_get](#do_get)|Fonction virtuelle appelée pour extraire une valeur numérique d'une séquence de caractères représentant une valeur monétaire.|
|[get](#get)|Extrait une valeur numérique d'une séquence de caractères représentant une valeur monétaire.|

## <a name="requirements"></a>spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="char_type"></a>  money_get::char_type

Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle *CharType*.

## <a name="do_get"></a>  money_get::do_get

Fonction virtuelle appelée pour extraire une valeur numérique d’une séquence de caractères qui représente une valeur monétaire.

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const
```

### <a name="parameters"></a>Paramètres

*premier* \
Itérateur d’entrée traitant le début de la séquence à convertir.

*dernier* \
Itérateur d’entrée traitant la fin de la séquence à convertir.

@No__t_1 *Intl*
Valeur booléenne indiquant le type de symbole monétaire attendu dans la séquence : **true** si international, **false** si national.

*Iosbase* \
Indicateur de format qui, quand il est défini, indique que le symbole monétaire est facultatif. Dans le cas contraire, il est obligatoire.

@No__t_1 d' *État*
Définit les éléments de masque de bits appropriés pour l’état de flux selon que les opérations ont réussi ou non.

\ *Val*
Chaîne stockant la séquence convertie.

### <a name="return-value"></a>Valeur de retour

Itérateur d’entrée qui traite le premier élément au-delà du champ d’entrée monétaire.

### <a name="remarks"></a>Notes

La première fonction membre protégée virtuelle tente de faire correspondre des éléments séquentiels en commençant au premier dans la séquence [ `first`, `last`) jusqu’à ce qu’elle ait reconnu un champ d’entrée monétaire complet et non vide. En cas de réussite, elle convertit ce champ en une séquence d’un ou de plusieurs chiffres décimaux, éventuellement précédée d’un signe moins (`-`), pour représenter le montant et stocke le résultat dans l’objet [STRING_TYPE](#string_type) *Val*. Elle retourne un itérateur désignant le premier élément au-delà du champ d’entrée monétaire. Dans le cas contraire, la fonction stocke une séquence vide dans *Val* et définit `ios_base::failbit` dans *État*. Elle retourne un itérateur désignant le premier élément au-delà de tout préfixe d’un champ d’entrée monétaire valide. Dans les deux cas, si la valeur de retour est égale à `last`, la fonction définit `ios_base::eofbit` dans `State`.

La deuxième fonction membre protégée virtuelle se comporte comme la première, sauf qu’en cas de réussite, elle convertit la séquence de chiffres éventuellement signée en une valeur de type **long double** et stocke cette valeur dans *Val*.

Le format d’un champ d’entrée monétaire est déterminé par la [facette de paramètres régionaux](../standard-library/locale-class.md#facet_class)**fac** retournée par l’appel effectif [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, **intl**>>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)).

Plus précisément :

- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) détermine l’ordre dans lequel les composants du champ se produisent.

- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) détermine la séquence d’éléments qui constitue un symbole monétaire.

- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) détermine la séquence d’éléments qui constitue un signe positif.

- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) détermine la séquence d’éléments qui constitue un signe négatif.

- **fac**. [grouping](../standard-library/moneypunct-class.md#grouping) détermine comment les chiffres sont regroupés à gauche de la virgule décimale.

- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) détermine l’élément qui sépare les groupes de chiffres à gauche de la virgule décimale.

- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) détermine l’élément qui sépare les chiffres entiers des chiffres de fraction.

- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) détermine le nombre de chiffres de fraction significatifs à droite de la virgule décimale. Lors de l’analyse d’un montant monétaire avec davantage de chiffres de fraction que `frac_digits` n’en demande, `do_get` arrête l’analyse après avoir consommé au plus `frac_digits` caractères.

Si la chaîne de signe ( **fac**. `negative_sign` ou **fac**. `positive_sign`) comporte plusieurs éléments, seul le premier élément est mis en correspondance là où l’élément égal à **money_base::sign** apparaît dans le modèle de format ( **fac**. `neg_format`). Les éléments restants sont mis en correspondance à la fin du champ d’entrée monétaire. Si aucune chaîne n’a un premier élément qui correspond à l’élément suivant dans le champ d’entrée monétaire, la chaîne de signe est considérée comme étant vide et le signe est positif.

Si **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) est différent de zéro, la chaîne **fac**. `curr_symbol` doit correspondre là où l’élément égal à **money_base::symbol** apparaît dans le modèle de format. Sinon, si **money_base::symbol** se produit à la fin du modèle de format, et s’il ne reste aucun élément de la chaîne de signe à mettre en correspondance, le symbole monétaire n’est pas mis en correspondance. Dans le cas contraire, le symbole monétaire est mis en correspondance de manière facultative.

Si aucune instance de **fac**. `thousands_sep` ne se produit dans la partie valeur du champ d’entrée monétaire (où l’élément égal à **money_base::value** apparaît dans le modèle de format), aucune contrainte de regroupement n’est imposée. Autrement, toute contrainte de regroupement imposée par **fac**. **grouping** est appliquée. Notez que la séquence de chiffres qui en résulte représente un entier dont les chiffres décimaux **fac**. `frac_digits` de poids faible sont considérés comme étant à droite de la virgule décimale.

Un espace blanc arbitraire est mis en correspondance là où l’élément égal à **money_base::space** apparaît dans le modèle de format, s’il apparaît à un emplacement autre que la fin du modèle de format. Dans le cas contraire, aucun espace blanc interne n’est mis en correspondance. Un élément *ch* est considéré comme un espace blanc si [use_facet](../standard-library/locale-functions.md#use_facet) < [ctype](../standard-library/ctype-class.md)\< **CharType**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). [is](../standard-library/ctype-class.md#is)( **ctype_base::space**, *ch*) a la valeur **true**.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [get](#get), qui appelle `do_get`.

## <a name="get"></a>  money_get::get

Extrait une valeur numérique d'une séquence de caractères représentant une valeur monétaire.

```cpp
iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const;

iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const;
```

### <a name="parameters"></a>Paramètres

*premier* \
Itérateur d’entrée traitant le début de la séquence à convertir.

*dernier* \
Itérateur d’entrée traitant la fin de la séquence à convertir.

@No__t_1 *Intl*
Valeur booléenne indiquant le type de symbole monétaire attendu dans la séquence : **true** si international, **false** si national.

*Iosbase* \
Indicateur de format qui, quand il est défini, indique que le symbole monétaire est facultatif. Dans le cas contraire, il est obligatoire.

@No__t_1 d' *État*
Définit les éléments de masque de bits appropriés pour l’état de flux selon que les opérations ont réussi ou non.

\ *Val*
Chaîne stockant la séquence convertie.

### <a name="return-value"></a>Valeur de retour

Itérateur d’entrée qui traite le premier élément au-delà du champ d’entrée monétaire.

### <a name="remarks"></a>Notes

Les deux fonctions membres retournent [do_get](#do_get) `(first, last, Intl, Iosbase, State, val)`.

### <a name="example"></a>Exemple

```cpp
// money_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;

int main( )
{
   locale loc( "german_germany" );

   basic_stringstream< char > psz;
   psz << use_facet<moneypunct<char, 1> >(loc).curr_symbol() << "-1.000,56";
   basic_stringstream< char > psz2;
   psz2 << "-100056" << use_facet<moneypunct<char, 1> >(loc).curr_symbol();

   ios_base::iostate st = 0;
   long double fVal;

   psz.flags( psz.flags( )|ios_base::showbase );
   // Which forced the READING the currency symbol
   psz.imbue(loc);
   use_facet < money_get < char > >( loc ).
      get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter( 0 ), true, psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get(" << psz.str( ) << ", intl = 1) FAILED"
           << endl;
   else
      cout << "money_get(" << psz.str( ) << ", intl = 1) = "
           << fVal/100.0 << endl;

   use_facet < money_get < char > >( loc ).
      get(basic_istream<char>::_Iter(psz2.rdbuf( )),
          basic_istream<char>::_Iter(0), false, psz2, st, fVal);

   if ( st & ios_base::failbit )
      cout << "money_get(" << psz2.str( ) << ", intl = 0) FAILED"
           << endl;
   else
      cout << "money_get(" << psz2.str( ) << ", intl = 0) = "
           << fVal/100.0 << endl;
};
```

## <a name="iter_type"></a>  money_get::iter_type

Type qui décrit un itérateur d'entrée.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle **InputIterator**.

## <a name="money_get"></a>  money_get::money_get

Constructeur des objets de type `money_get` utilisés pour extraire des valeurs numériques de séquences représentant des valeurs monétaires.

```cpp
explicit money_get(size_t _Refs = 0);
```

### <a name="parameters"></a>Paramètres

*_Refs* \
Valeur entière utilisée pour spécifier le type de gestion de mémoire pour l’objet.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le paramètre *_Refs* et leur signification sont les suivantes :

- 0 : la durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : la durée de vie de l’objet doit être gérée manuellement.

- \> 1 : ces valeurs ne sont pas définies.

Aucun exemple direct n’est possible, car le destructeur est protégé.

Le constructeur initialise son objet de base avec **locale ::** [facette](../standard-library/locale-class.md#facet_class)( *_Refs*).

## <a name="string_type"></a>  money_get::string_type

Type qui décrit une chaîne contenant des caractères de type **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [basic_string](../standard-library/basic-string-class.md).

## <a name="see-also"></a>Voir aussi

[\<locale>](../standard-library/locale.md)\
[facet, classe](../standard-library/locale-class.md#facet_class)\
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
