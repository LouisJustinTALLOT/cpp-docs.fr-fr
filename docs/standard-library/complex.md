---
title: '&lt;complex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <complex>
- std::<complex>
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
ms.openlocfilehash: 585f970f1a3482412ff225454b7acce9060e2d7c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449432"
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

Définit la classe `complex` de modèle de conteneur et ses modèles de prise en charge.

## <a name="requirements"></a>Configuration requise

**En-tête** : \<complex>

**Espace de noms :** std

## <a name="remarks"></a>Notes

Un nombre complexe est une paire ordonnée de nombres réels. En termes purement géométriques, le plan complexe est le plan réel à deux dimensions. Les qualités spéciales du plan complexe qui le distinguent du plan réel sont dues au fait qu'il a une structure algébrique supplémentaire. Cette structure algébrique a deux opérations fondamentales :

- Addition définie comme (*a*, *b*) + (*c*, *d*) = (*a* + *c*, *b* + *d*)

- Multiplication définie comme (*a*, *b*) \* (*c*, *d*) = (*AC* - *BD*, *ad* + *BC*)

L'ensemble de nombres complexes avec les opérations d'addition complexe et de multiplication complexe est un domaine au sens algébrique standard :

- Les opérations d'addition et multiplication sont commutatives et associatives, et la multiplication se distribue sur l'addition exactement comme elle le fait avec l'addition et la multiplication de réels sur le domaine des nombres réels.

- Le nombre complexe (0, 0) est l’identité additive et (1, 0) est l’identité multiplicative.

- L’inverse additif pour un nombre complexe (*a*, *b*) est (-*a*,-*b*) et l’inverse multiplicatif pour tous les nombres complexes, à l’exception de (0, 0) est

   (*a*/(*a*<sup>2</sup> + *b*<sup>2</sup>), -*b*/(*a*<sup>2</sup> + *b*<sup>2</sup>))

En représentant un nombre complexe *z* = (*a*, *b*) sous la forme *z* = *a* + *bi*, où *i*<sup>2</sup> =-1, les règles de l’algèbre de l’ensemble des nombres réels peuvent être appliquées au ensemble de nombres complexes et à leurs composants. Par exemple :

   (1 + 2*i*)  \* \* <sup></sup>    (2 + 3 i) = 1 (2 + 3 i) + 2 i (2 + 3 i) = (2 + 3 i) + (4 i + 6 i 2) = (2-6) + (3 + 4) i =-4 + 7 i \*

Le système des nombres complexes est un domaine, mais il n'est pas un domaine ordonné. Il n’y a pas d’ordre des nombres complexes, en ce qui concerne le champ des nombres réels et de ses sous-ensembles. les inégalités ne peuvent donc pas être appliquées aux nombres complexes comme c’est le cas des nombres réels.

Il existe trois formes courantes de représentation d’un nombre complexe *z* :

- Cartésien: *z* = a*bi*  + 

- Polaire: *z* = *r* (COS *p* + *i* Sin *p*)

- Exponentiel: *z* = *r* \* *e*<sup>*IP*</sup>

Les termes utilisés dans ces représentations standard d'un nombre complexe s'entendent comme suit :

- Le composant cartésien réel ou la partie réelle *a*.

- Le composant cartésien imaginaire ou la partie imaginaire *b*.

- Le modulo ou la valeur absolue d’un nombre complexe *r*.

- Argument ou angle de phase *p* en radians.

Sauf indication contraire, les fonctions qui peuvent retourner plusieurs valeurs sont requises pour retourner une valeur principale pour leurs arguments supérieur à-π et inférieure ou égale à + π pour les conserver à valeur unique. Tous les angles doivent être exprimés en radians, où il y a 2π radians (360 degrés) dans un cercle.

## <a name="members"></a>Membres

### <a name="functions"></a>Fonctions

|||
|-|-|
|[abs](../standard-library/complex-functions.md#abs)|Calcule le module d'un nombre complexe.|
|[acos](../standard-library/complex-functions.md#acos)||
|[acosh](../standard-library/complex-functions.md#acosh)||
|[arg](../standard-library/complex-functions.md#arg)|Extrait l’argument d’un nombre complexe.|
|[asin](../standard-library/complex-functions.md#asin)||
|[asinh](../standard-library/complex-functions.md#asinh)||
|[atan](../standard-library/complex-functions.md#atan)||
|[atanh](../standard-library/complex-functions.md#atanh)||
|[conj](../standard-library/complex-functions.md#conj)|Retourne le conjugué complexe d'un nombre complexe.|
|[cos](../standard-library/complex-functions.md#cos)|Retourne le cosinus d'un nombre complexe.|
|[cosh](../standard-library/complex-functions.md#cosh)|Retourne le cosinus hyperbolique d'un nombre complexe.|
|[exp](../standard-library/complex-functions.md#exp)|Retourne la fonction exponentielle d'un nombre complexe.|
|[imag](../standard-library/complex-functions.md#imag)|Extrait le composant imaginaire d'un nombre complexe.|
|[log](../standard-library/complex-functions.md#log)|Retourne le logarithme naturel d'un nombre complexe.|
|[log10](../standard-library/complex-functions.md#log10)|Retourne le logarithme de base 10 d'un nombre complexe.|
|[norm](../standard-library/complex-functions.md#norm)|Extrait la norme d'un nombre complexe.|
|[polar](../standard-library/complex-functions.md#polar)|Retourne le nombre complexe qui correspond à un module et à un argument spécifiés, au format cartésien.|
|[pow](../standard-library/complex-functions.md#pow)|Évalue le nombre complexe obtenu en élevant une base qui est un nombre complexe à la puissance d'un autre nombre complexe.|
|[proj](../standard-library/complex-functions.md#proj)||
|[real](../standard-library/complex-functions.md#real)|Extrait le composant réel d'un nombre complexe.|
|[sin](../standard-library/complex-functions.md#sin)|Retourne le sinus d'un nombre complexe.|
|[sinh](../standard-library/complex-functions.md#sinh)|Retourne le sinus hyperbolique d'un nombre complexe.|
|[sqrt](../standard-library/complex-functions.md#sqrt)|Retourne la racine carrée d'un nombre complexe.|
|[tan](../standard-library/complex-functions.md#tan)|Retourne la tangente d'un nombre complexe.|
|[tanh](../standard-library/complex-functions.md#tanh)|Retourne la tangente hyperbolique d'un nombre complexe.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[!=, opérateur](../standard-library/complex-operators.md#op_neq)|Vérifie l'inégalité entre deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[operator*](../standard-library/complex-operators.md#op_star)|Multiplie deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[operator+](../standard-library/complex-operators.md#op_add)|Additionne deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[operator-](../standard-library/complex-operators.md#operator-)|Soustrait deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[operator/](../standard-library/complex-operators.md#op_div)|Divise deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[operator<\<](../standard-library/complex-operators.md#op_lt_lt)|Fonction de modèle qui insère un nombre complexe dans le flux de sortie.|
|[operator==](../standard-library/complex-operators.md#op_eq_eq)|Vérifie l'égalité entre deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[operator>>](../standard-library/complex-operators.md#op_gt_gt)|Fonction de modèle qui extrait un nombre complexe du flux d'entrée.|

### <a name="classes"></a>Classes

|||
|-|-|
|[complex\<double>](../standard-library/complex-double.md)|La classe de modèle explicitement spécialisée décrit un objet qui stocke une paire ordonnée d’objets, tous deux de type **double**, où le premier représente la partie réelle d’un nombre complexe et le second représente la partie imaginaire.|
|[complex\<float>](../standard-library/complex-float.md)|La classe de modèle explicitement spécialisée décrit un objet qui stocke une paire ordonnée d’objets, tous deux de type **float**, où le premier représente la partie réelle d’un nombre complexe et le second représente la partie imaginaire.|
|[complex\<long double>](../standard-library/complex-long-double.md)|La classe de modèle explicitement spécialisée décrit un objet qui stocke une paire ordonnée d’objets, tous deux de type **long double**, où le premier représente la partie réelle d’un nombre complexe et le second représente la partie imaginaire.|
|[complex](../standard-library/complex-class.md)|La classe de modèle décrit un objet utilisé pour représenter le système des nombres complexes et pour effectuer des opérations arithmétiques complexes.|

### <a name="literals"></a>Littéraux

L’en-tête \<complex> définit les [littéraux définis par l’utilisateur](../cpp/user-defined-literals-cpp.md) suivants, qui créent un nombre complexe avec la partie réelle équivalant à zéro et la partie imaginaire étant la valeur du paramètre d’entrée.

|||
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br />`constexpr complex<long double> operator""il(unsigned long long d)`|Cette`complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br />`constexpr complex<double> operator""i(unsigned long long d)`|Retourne : `complex<double>{0.0, static_cast<double>(d)}`.|
|`constexpr complex<float> operator""if(long double d)`<br />`constexpr complex<float> operator""if(unsigned long long d)`|Retourne : `complex<float>{0.0f, static_cast<float>(d)}`.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
