---
title: moneypunct, classe
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct
- xlocmon/std::moneypunct::char_type
- xlocmon/std::moneypunct::string_type
- xlocmon/std::moneypunct::curr_symbol
- xlocmon/std::moneypunct::decimal_point
- xlocmon/std::moneypunct::do_curr_symbol
- xlocmon/std::moneypunct::do_decimal_point
- xlocmon/std::moneypunct::do_frac_digits
- xlocmon/std::moneypunct::do_grouping
- xlocmon/std::moneypunct::do_neg_format
- xlocmon/std::moneypunct::do_negative_sign
- xlocmon/std::moneypunct::do_pos_format
- xlocmon/std::moneypunct::do_positive_sign
- xlocmon/std::moneypunct::do_thousands_sep
- xlocmon/std::moneypunct::frac_digits
- xlocmon/std::moneypunct::grouping
- xlocmon/std::moneypunct::neg_format
- xlocmon/std::moneypunct::negative_sign
- xlocmon/std::moneypunct::pos_format
- xlocmon/std::moneypunct::positive_sign
- xlocmon/std::moneypunct::thousands_sep
helpviewer_keywords:
- std::moneypunct [C++]
- std::moneypunct [C++], char_type
- std::moneypunct [C++], string_type
- std::moneypunct [C++], curr_symbol
- std::moneypunct [C++], decimal_point
- std::moneypunct [C++], do_curr_symbol
- std::moneypunct [C++], do_decimal_point
- std::moneypunct [C++], do_frac_digits
- std::moneypunct [C++], do_grouping
- std::moneypunct [C++], do_neg_format
- std::moneypunct [C++], do_negative_sign
- std::moneypunct [C++], do_pos_format
- std::moneypunct [C++], do_positive_sign
- std::moneypunct [C++], do_thousands_sep
- std::moneypunct [C++], frac_digits
- std::moneypunct [C++], grouping
- std::moneypunct [C++], neg_format
- std::moneypunct [C++], negative_sign
- std::moneypunct [C++], pos_format
- std::moneypunct [C++], positive_sign
- std::moneypunct [C++], thousands_sep
ms.assetid: cf2650da-3e6f-491c-95d5-23e57f582ee6
ms.openlocfilehash: 7960ee8b5e9ce6b27494e896e38bbf6b5256fe7e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689296"
---
# <a name="moneypunct-class"></a>moneypunct, classe

Le modèle de classe décrit un objet pouvant servir de facette de paramètres régionaux pour décrire les séquences de type *CharType* utilisées pour représenter un champ d’entrée monétaire ou un champ de sortie monétaire. Si le paramètre de modèle *Intl* a la *valeur true*, les conventions internationales sont respectées.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, bool Intl>
class moneypunct;
```

### <a name="parameters"></a>Paramètres

*CharType* \
Type utilisé dans le cadre d'un programme pour encoder des caractères.

@No__t_1 *Intl*
Indicateur spécifiant si les conventions internationales doivent être respectées.

## <a name="remarks"></a>Notes

Comme avec n'importe quelle facette de paramètres régionaux, l'ID d'objet statique possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans **id.**

L’objet statique const intl stocke la valeur du paramètre de modèle *Intl*.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[moneypunct](#moneypunct)|Constructeur d'objets de type `moneypunct`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.|
|[string_type](#string_type)|Type qui décrit une chaîne contenant des caractères de type `CharType`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[curr_symbol](#curr_symbol)|Retourne une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole monétaire.|
|[decimal_point](#decimal_point)|Retourne une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole de virgule décimale.|
|[do_curr_symbol](#do_curr_symbol)|Fonction membre virtuelle protégée qui retourne une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole monétaire.|
|[do_decimal_point](#do_decimal_point)|Fonction membre virtuelle protégée qui est appelée pour retourner une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole de virgule décimale.|
|[do_frac_digits](#do_frac_digits)|Cette fonction membre virtuelle protégée retourne un compte spécifique aux paramètres régionaux du nombre de chiffres à afficher à droite de la virgule décimale.|
|[do_grouping](#do_grouping)|Cette fonction membre virtuelle protégée retourne une règle spécifique aux paramètres régionaux permettant de déterminer la manière dont les chiffres sont regroupés à gauche de la virgule décimale.|
|[do_neg_format](#do_neg_format)|Fonction membre virtuelle protégée qui est appelée pour retourner une règle spécifique aux paramètres régionaux pour mettre en forme les sorties avec des montants négatifs.|
|[do_negative_sign](#do_negative_sign)|Fonction membre virtuelle protégée qui est appelée pour retourner une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole du signe négatif.|
|[do_pos_format](#do_pos_format)|Fonction membre virtuelle protégée qui est appelée pour retourner une règle spécifique aux paramètres régionaux pour mettre en forme les sorties avec des montants positifs.|
|[do_positive_sign](#do_positive_sign)|Fonction membre virtuelle protégée qui est appelée pour retourner une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole du signe positif.|
|[do_thousands_sep](#do_thousands_sep)|Fonction membre virtuelle protégée qui est appelée pour retourner une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole de séparateur des milliers.|
|[frac_digits](#frac_digits)|Retourne un compte spécifique aux paramètres régionaux du nombre de chiffres à afficher à droite de la virgule décimale.|
|[grouping](#grouping)|Retourne une règle spécifique aux paramètres régionaux pour déterminer la manière dont les chiffres sont regroupés à gauche de la virgule décimale.|
|[neg_format](#neg_format)|Retourne une règle spécifique aux paramètres régionaux pour mettre en forme les sorties avec des montants négatifs.|
|[negative_sign](#negative_sign)|Retourne une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole du signe négatif.|
|[pos_format](#pos_format)|Retourne une règle spécifique aux paramètres régionaux pour mettre en forme les sorties avec des montants positifs.|
|[positive_sign](#positive_sign)|Retourne une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole du signe positif.|
|[thousands_sep](#thousands_sep)|Retourne une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole de séparateur des milliers.|

## <a name="requirements"></a>spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="char_type"></a>  moneypunct::char_type

Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle **CharType**.

## <a name="curr_symbol"></a>  moneypunct::curr_symbol

Retourne une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole monétaire.

```cpp
string_type curr_symbol() const;
```

### <a name="return-value"></a>Valeur de retour

Chaîne contenant le symbole monétaire.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_curr_symbol](#do_curr_symbol).

### <a name="example"></a>Exemple

```cpp
// moneypunct_curr_symbol.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct < char, true > &mpunct = use_facet < moneypunct < char, true > >(loc);
   cout << loc.name( ) << " international currency symbol "<<  mpunct.curr_symbol( ) << endl;

   const moneypunct < char, false> &mpunct2 = use_facet < moneypunct < char, false> >(loc);
   cout << loc.name( ) << " domestic currency symbol "<<  mpunct2.curr_symbol( ) << endl;
};
```

## <a name="decimal_point"></a>  moneypunct::decimal_point

Retourne une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole de virgule décimale.

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>Valeur de retour

Séquence propre aux paramètres régionaux d’éléments à utiliser comme symbole de virgule décimale.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_decimal_point](#do_decimal_point).

### <a name="example"></a>Exemple

```cpp
// moneypunct_decimal_pt.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc("german_germany");

   const moneypunct < char, true > &mpunct = use_facet
      < moneypunct < char, true > >(loc);
   cout << loc.name( ) << " international decimal point "
        << mpunct.decimal_point( ) << endl;

   const moneypunct < char, false> &mpunct2 = use_facet
      < moneypunct < char, false> >(loc);
   cout << loc.name( ) << " domestic decimal point "
        << mpunct2.decimal_point( ) << endl;
}
```

```Output
German_Germany.1252 international decimal point ,
German_Germany.1252 domestic decimal point ,
```

## <a name="do_curr_symbol"></a>  moneypunct::do_curr_symbol

Fonction membre virtuelle protégée qui retourne une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole monétaire.

```cpp
virtual string_type do_curr_symbol() const;
```

### <a name="return-value"></a>Valeur de retour

Séquence propre aux paramètres régionaux d’éléments à utiliser comme symbole de virgule décimale.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [curr_symbol](#curr_symbol), où la fonction membre virtuelle est appelée par `curr_symbol`.

## <a name="do_decimal_point"></a>  moneypunct::do_decimal_point

Fonction membre virtuelle protégée qui retourne une séquence propre aux paramètres régionaux d’éléments à utiliser comme symbole de virgule décimale.

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>Valeur de retour

Séquence propre aux paramètres régionaux d’éléments à utiliser comme symbole de virgule décimale.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [decimal_point](#decimal_point), où la fonction membre virtuelle est appelée par `decimal_point`.

## <a name="do_frac_digits"></a>  moneypunct::do_frac_digits

Fonction membre virtuelle protégée qui retourne un décompte propre aux paramètres régionaux du nombre de chiffres à afficher à droite de la virgule décimale.

```cpp
virtual int do_frac_digits() const;
```

### <a name="return-value"></a>Valeur de retour

Décompte propre aux paramètres régionaux du nombre de chiffres à afficher à droite de la virgule décimale.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [frac_digits](#frac_digits), où la fonction membre virtuelle est appelée par `frac_digits`.

## <a name="do_grouping"></a>  moneypunct::do_grouping

Fonction membre virtuelle protégée qui retourne une règle propre aux paramètres régionaux permettant de déterminer comment les chiffres sont regroupés à gauche de la virgule décimale.

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>Valeur de retour

Règle propre aux paramètres régionaux pour déterminer comment les chiffres sont regroupés à gauche de la virgule décimale.

### <a name="example"></a>Exemple

Consultez l’exemple de [regroupement](#grouping), où la fonction membre virtuelle est appelée par `grouping`.

## <a name="do_neg_format"></a>  moneypunct::do_neg_format

Fonction membre virtuelle protégée qui est appelée pour retourner une règle spécifique aux paramètres régionaux pour mettre en forme les sorties avec des montants négatifs.

```cpp
virtual pattern do_neg_format() const;
```

### <a name="return-value"></a>Valeur de retour

La fonction membre virtuelle protégée retourne une règle propre aux paramètres régionaux pour déterminer comment générer un champ de sortie monétaire pour un montant négatif. Chacun des quatre éléments de `pattern::field` peut avoir les valeurs suivantes :

- `none` pour qu’il corresponde à zéro ou plusieurs espaces ou ne génère rien.

- `sign` de correspondance ou de génération d’un signe positif ou négatif.

- `space` pour qu’il corresponde à zéro ou plusieurs espaces ou pour générer un espace.

- `symbol` pour la correspondance ou la génération d’un symbole monétaire.

- `value` pour la correspondance ou la génération d’une valeur monétaire.

Les composants d’un champ de sortie monétaire sont générés et les composants d’un champ d’entrée monétaire sont mis en correspondance dans l’ordre dans lequel ces éléments apparaissent dans `pattern::field`. Chacune des valeurs `sign`, `symbol`, `value` et `none` ou `space` doit apparaître exactement une fois. La valeur `none` ne doit pas apparaître en premier. La valeur space **ne doit pas** apparaître en premier ou en dernier. Si `Intl` a la valeur true, l’ordre est `symbol`, `sign`, `none`, puis `value`.

La version de modèle de `moneypunct`\< **CharType**, **Intl**> retourne `{`**money_base::symbol**, **money_base::sign**, **money_base::value**, **money_base::none**`}`.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [neg_format](#neg_format), où la fonction membre virtuelle est appelée par `neg_format`.

## <a name="do_negative_sign"></a>  moneypunct::do_negative_sign

Fonction membre virtuelle protégée qui est appelée pour retourner une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole du signe négatif.

```cpp
virtual string_type do_negative_sign() const;
```

### <a name="return-value"></a>Valeur de retour

Séquence propre aux paramètres régionaux d’éléments à utiliser comme signe négatif.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [negative_sign](#negative_sign), où la fonction membre virtuelle est appelée par `negative_sign`.

## <a name="do_pos_format"></a>  moneypunct::do_pos_format

Fonction membre virtuelle protégée qui est appelée pour retourner une règle spécifique aux paramètres régionaux pour mettre en forme les sorties avec des montants positifs.

```cpp
virtual pattern do_pos_format() const;
```

### <a name="return-value"></a>Valeur de retour

La fonction membre virtuelle protégée retourne une règle propre aux paramètres régionaux pour déterminer comment générer un champ de sortie monétaire pour un montant positif. (Il détermine également comment faire correspondre les composants d’un champ d’entrée monétaire.) L’encodage est le même que pour [do_neg_format](#do_neg_format).

La version de modèle de moneypunct\< **CharType**, **Inputlterator**> retourne `{`**money_base::symbol**, **money_base::sign**, **money_base::value**, **money_base::none**`}`.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [pos_format](#pos_format), où la fonction membre virtuelle est appelée par `pos_format`.

## <a name="do_positive_sign"></a>  moneypunct::do_positive_sign

Fonction membre virtuelle protégée qui retourne une séquence propre aux paramètres régionaux d’éléments à utiliser comme signe positif.

```cpp
virtual string_type do_positive_sign() const;
```

### <a name="return-value"></a>Valeur de retour

Séquence propre aux paramètres régionaux d’éléments à utiliser comme signe positif.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [positive_sign](#positive_sign), où la fonction membre virtuelle est appelée par `positive_sign`.

## <a name="do_thousands_sep"></a>  moneypunct::do_thousands_sep

Fonction membre virtuelle protégée qui retourne un élément propre aux paramètres régionaux à utiliser comme séparateur de groupes à gauche de la virgule décimale.

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>Valeur de retour

Élément propre aux paramètres régionaux à utiliser comme séparateur de groupes à gauche de la virgule décimale.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [thousands_sep](#thousands_sep), où la fonction membre virtuelle est appelée par `thousands_sep`.

## <a name="frac_digits"></a>  moneypunct::frac_digits

Retourne un compte spécifique aux paramètres régionaux du nombre de chiffres à afficher à droite de la virgule décimale.

```cpp
int frac_digits() const;
```

### <a name="return-value"></a>Valeur de retour

Décompte propre aux paramètres régionaux du nombre de chiffres à afficher à droite de la virgule décimale.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_frac_digits](#do_frac_digits).

### <a name="example"></a>Exemple

```cpp
// moneypunct_frac_digits.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true> >(loc);
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " international frac_digits\n to the right"
        << " of the radix character: "
        << mpunct.frac_digits ( ) << endl << endl;

   const moneypunct <char, false> &mpunct2 =
       use_facet <moneypunct <char, false> >(loc);
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " domestic grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct2.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " domestic frac_digits\n to the right"
        << " of the radix character: "
        << mpunct2.frac_digits ( ) << endl << endl;
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 international frac_digits
to the right of the radix character: 2

German_Germany.1252 domestic grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 domestic frac_digits
to the right of the radix character: 2
```

## <a name="grouping"></a>  moneypunct::grouping

Retourne une règle spécifique aux paramètres régionaux pour déterminer la manière dont les chiffres sont regroupés à gauche de la virgule décimale.

```cpp
string grouping() const;
```

### <a name="return-value"></a>Valeur de retour

Règle propre aux paramètres régionaux pour déterminer comment les chiffres sont regroupés à gauche de la virgule décimale.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_grouping](#do_grouping).

### <a name="example"></a>Exemple

```cpp
// moneypunct_grouping.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true> >( loc );
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " international frac_digits\n to the right"
        << " of the radix character: "
        << mpunct.frac_digits ( ) << endl << endl;

   const moneypunct <char, false> &mpunct2 =
       use_facet <moneypunct <char, false> >( loc );
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " domestic grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct2.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " domestic frac_digits\n to the right"
        << " of the radix character: "
        << mpunct2.frac_digits ( ) << endl << endl;
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 international frac_digits
to the right of the radix character: 2

German_Germany.1252 domestic grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 domestic frac_digits
to the right of the radix character: 2
```

## <a name="moneypunct"></a>  moneypunct::moneypunct

Constructeur d'objets de type `moneypunct`.

```cpp
explicit moneypunct(size_t _Refs = 0);
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

Le constructeur initialise son objet de base avec [locale::facet](../standard-library/locale-class.md#facet_class)(_ *Refs*).

## <a name="neg_format"></a>  moneypunct::neg_format

Retourne une règle spécifique aux paramètres régionaux pour mettre en forme les sorties avec des montants négatifs.

```cpp
pattern neg_format() const;
```

### <a name="return-value"></a>Valeur de retour

Règle propre aux paramètres régionaux pour mettre en forme les sorties avec des montants négatifs.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_neg_format](#do_neg_format).

### <a name="example"></a>Exemple

```cpp
// moneypunct_neg_format.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( ) {
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international negative number format: "
        << mpunct.neg_format( ).field[0]
        << mpunct.neg_format( ).field[1]
        << mpunct.neg_format( ).field[2]
        << mpunct.neg_format( ).field[3] << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic negative number format: "
        << mpunct2.neg_format( ).field[0]
        << mpunct2.neg_format( ).field[1]
        << mpunct2.neg_format( ).field[2]
        << mpunct2.neg_format( ).field[3] << endl;
}
```

## <a name="negative_sign"></a>  moneypunct::negative_sign

Retourne une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole du signe négatif.

```cpp
string_type negative_sign() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole du signe négatif.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_negative_sign](#do_negative_sign).

### <a name="example"></a>Exemple

```cpp
// moneypunct_neg_sign.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true> >(loc);
   cout << loc.name( ) << " international negative sign: "
        << mpunct.negative_sign( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic negative sign: "
        << mpunct2.negative_sign( ) << endl;

   locale loc2( "French" );

   const moneypunct <char, true> &mpunct3 =
      use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international negative sign: "
        << mpunct3.negative_sign( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic negative sign: "
        << mpunct4.negative_sign( ) << endl;
};
```

```Output
German_Germany.1252 international negative sign: -
German_Germany.1252 domestic negative sign: -
French_France.1252 international negative sign: -
French_France.1252 domestic negative sign: -
```

## <a name="pos_format"></a>  moneypunct::pos_format

Retourne une règle spécifique aux paramètres régionaux pour mettre en forme les sorties avec des montants positifs.

```cpp
pattern pos_format() const;
```

### <a name="return-value"></a>Valeur de retour

Règle propre aux paramètres régionaux pour mettre en forme les sorties avec des montants positifs.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_pos_format](#do_pos_format).

### <a name="example"></a>Exemple

```cpp
// moneypunct_pos_format.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main() {
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true> >(loc);
   cout << loc.name( ) << " international positive number format: "
        << mpunct.pos_format( ).field[0]
        << mpunct.pos_format( ).field[1]
        << mpunct.pos_format( ).field[2]
        << mpunct.pos_format( ).field[3] << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic positive number format: "
        << mpunct2.pos_format( ).field[0]
        << mpunct2.pos_format( ).field[1]
        << mpunct2.pos_format( ).field[2]
        << mpunct2.pos_format( ).field[3] << endl;
}
```

## <a name="positive_sign"></a>  moneypunct::positive_sign

Retourne une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole du signe positif.

```cpp
string_type positive_sign() const;
```

### <a name="return-value"></a>Valeur de retour

Séquence propre aux paramètres régionaux d’éléments à utiliser comme symbole du signe positif.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_positive_sign](#do_positive_sign).

### <a name="example"></a>Exemple

```cpp
// moneypunct_pos_sign.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international positive sign:"
        << mpunct.positive_sign( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic positive sign:"
        << mpunct2.positive_sign( ) << endl;

   locale loc2( "French" );

   const moneypunct <char, true> &mpunct3 =
      use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international positive sign:"
        << mpunct3.positive_sign( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic positive sign:"
        << mpunct4.positive_sign( ) << endl;
};
```

```Output
German_Germany.1252 international positive sign:
German_Germany.1252 domestic positive sign:
French_France.1252 international positive sign:
French_France.1252 domestic positive sign:
```

## <a name="string_type"></a>  moneypunct::string_type

Type qui décrit une chaîne contenant des caractères de type **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation du modèle de classe [basic_string](../standard-library/basic-string-class.md) dont les objets peuvent stocker des copies des séquences de ponctuation.

## <a name="thousands_sep"></a>  moneypunct::thousands_sep

Retourne une séquence spécifique aux paramètres régionaux d'éléments à utiliser comme symbole de séparateur des milliers.

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>Valeur de retour

Séquence propre aux paramètres régionaux d’éléments à utiliser comme séparateur des milliers.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_thousands_sep](#do_thousands_sep).

### <a name="example"></a>Exemple

```cpp
// moneypunct_thou_sep.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international thousands separator: "
        << mpunct.thousands_sep( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic thousands separator: "
        << mpunct2.thousands_sep( ) << endl << endl;

   locale loc2( "english_canada" );

   const moneypunct <char, true> &mpunct3 =
       use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international thousands separator: "
        << mpunct3.thousands_sep( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic thousands separator: "
        << mpunct4.thousands_sep( ) << endl;
}
```

```Output
German_Germany.1252 international thousands separator: .
German_Germany.1252 domestic thousands separator: .

English_Canada.1252 international thousands separator: ,
English_Canada.1252 domestic thousands separator: ,
```

## <a name="see-also"></a>Voir aussi

[\<locale>](../standard-library/locale.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
