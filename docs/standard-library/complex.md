---
description: 'En savoir plus sur : &lt; complexe&gt;'
title: '&lt;complex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <complex>
- std::<complex>
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
ms.openlocfilehash: b16798cf1725ba6fa681b04f735d44f02a2b1b82
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233836"
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

Définit le modèle de classe `complex` de conteneur et ses modèles de prise en charge.

## <a name="requirements"></a>Spécifications

**En-tête**: \<complex>

**Espace de noms :** std

## <a name="remarks"></a>Notes

Un nombre complexe est une paire ordonnée de nombres réels. En termes purement géométriques, le plan complexe est le plan réel à deux dimensions. Les qualités spéciales du plan complexe qui le distinguent du plan réel sont dues au fait qu'il a une structure algébrique supplémentaire. Cette structure algébrique a deux opérations fondamentales :

- Addition définie comme (*a*, *b*) + (*c*, *d*) = (*a*  +  *c*, *b*  +  *d*)

- Multiplication définie comme (*a*, *b*) \* (*c*, *d*) = (*AC*  -  *BD*, *ad*  +  *BC*)

L'ensemble de nombres complexes avec les opérations d'addition complexe et de multiplication complexe est un domaine au sens algébrique standard :

- Les opérations d'addition et multiplication sont commutatives et associatives, et la multiplication se distribue sur l'addition exactement comme elle le fait avec l'addition et la multiplication de réels sur le domaine des nombres réels.

- Le nombre complexe (0, 0) est l'identité additive et (1, 0) est l'identité multiplicative.

- L’inverse additif pour un nombre complexe (*a*, *b*) est (-*a*,-*b*) et l’inverse multiplicatif pour tous les nombres complexes, à l’exception de (0, 0) est

   (*a*/(*a*<sup>2</sup>  +  *b*<sup>2</sup>),-*b*/(*a*<sup>2</sup>  +  *b*<sup>2</sup>))

En représentant un nombre complexe *z* = (*a*, *b*) sous la forme *z*  =  *a*  +  *bi*, où *i*<sup>2</sup> =-1, les règles de l’algèbre de l’ensemble des nombres réels peuvent être appliquées à l’ensemble de nombres complexes et à leurs composants. Par exemple :

   (1 + 2 *i*) \* (2 + 3 *i*) = 1 \* (2 + 3 *i*) + 2 *i* \* (2 + 3 *i*) = (2 + 3 *i*) + (4 *i* + 6 *i*<sup>2</sup>) = (2-6) + (3 + 4)*i* =-4 + 7 *i*

Le système des nombres complexes est un domaine, mais il n'est pas un domaine ordonné. Il n’y a pas d’ordre des nombres complexes, en ce qui concerne le champ des nombres réels et de ses sous-ensembles. les inégalités ne peuvent donc pas être appliquées aux nombres complexes comme c’est le cas des nombres réels.

Il existe trois formes courantes de représentation d’un nombre complexe *z* :

- Cartésien : *z*  =  *a*  +  *bi*

- Polaire : *z*  =  *r* (COS *p*  +  *i* Sin *p*)

- Exponentiel : *z*  =  *r* \* *e*<sup>*IP*</sup>

Les termes utilisés dans ces représentations standard d'un nombre complexe s'entendent comme suit :

- Le composant cartésien réel ou la partie réelle *a*.

- Le composant cartésien imaginaire ou la partie imaginaire *b*.

- Le modulo ou la valeur absolue d’un nombre complexe *r*.

- Argument ou angle de phase *p* en radians.

Sauf indication contraire, les fonctions qui peuvent retourner plusieurs valeurs sont requises pour retourner une valeur principale pour leurs arguments supérieur à-π et inférieure ou égale à + π pour les conserver à valeur unique. Tous les angles doivent être exprimés en radians, où il y a 2π radians (360 degrés) dans un cercle.

## <a name="members"></a>Membres

### <a name="functions"></a>Fonctions

|Nom|Description|
|-|-|
|[absolue](../standard-library/complex-functions.md#abs)|Calcule le module d'un nombre complexe.|
|[ACOS](../standard-library/complex-functions.md#acos)||
|[acosh](../standard-library/complex-functions.md#acosh)||
|[donnée](../standard-library/complex-functions.md#arg)|Extrait l’argument d’un nombre complexe.|
|[ASIN](../standard-library/complex-functions.md#asin)||
|[asinh](../standard-library/complex-functions.md#asinh)||
|[atan](../standard-library/complex-functions.md#atan)||
|[ATANH](../standard-library/complex-functions.md#atanh)||
|[conj](../standard-library/complex-functions.md#conj)|Retourne le conjugué complexe d'un nombre complexe.|
|[COS](../standard-library/complex-functions.md#cos)|Retourne le cosinus d'un nombre complexe.|
|[cosh](../standard-library/complex-functions.md#cosh)|Retourne le cosinus hyperbolique d'un nombre complexe.|
|[exp](../standard-library/complex-functions.md#exp)|Retourne la fonction exponentielle d'un nombre complexe.|
|[imag](../standard-library/complex-functions.md#imag)|Extrait le composant imaginaire d'un nombre complexe.|
|[Sign](../standard-library/complex-functions.md#log)|Retourne le logarithme naturel d'un nombre complexe.|
|[log10](../standard-library/complex-functions.md#log10)|Retourne le logarithme de base 10 d'un nombre complexe.|
|[norm](../standard-library/complex-functions.md#norm)|Extrait la norme d'un nombre complexe.|
|[polarisé](../standard-library/complex-functions.md#polar)|Retourne le nombre complexe qui correspond à un module et à un argument spécifiés, au format cartésien.|
|[Poe](../standard-library/complex-functions.md#pow)|Évalue le nombre complexe obtenu en élevant une base qui est un nombre complexe à la puissance d'un autre nombre complexe.|
|[proj](../standard-library/complex-functions.md#proj)||
|[real](../standard-library/complex-functions.md#real)|Extrait le composant réel d'un nombre complexe.|
|[Sin](../standard-library/complex-functions.md#sin)|Retourne le sinus d'un nombre complexe.|
|[Sinh](../standard-library/complex-functions.md#sinh)|Retourne le sinus hyperbolique d'un nombre complexe.|
|[racine](../standard-library/complex-functions.md#sqrt)|Retourne la racine carrée d'un nombre complexe.|
|[Tan](../standard-library/complex-functions.md#tan)|Retourne la tangente d'un nombre complexe.|
|[Tanh](../standard-library/complex-functions.md#tanh)|Retourne la tangente hyperbolique d'un nombre complexe.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur ! =](../standard-library/complex-operators.md#op_neq)|Vérifie l'inégalité entre deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[and](../standard-library/complex-operators.md#op_star)|Multiplie deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[opérateur +](../standard-library/complex-operators.md#op_add)|Additionne deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[and](../standard-library/complex-operators.md#operator-)|Soustrait deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[and](../standard-library/complex-operators.md#op_div)|Divise deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[<d’opérateur \<](../standard-library/complex-operators.md#op_lt_lt)|Fonction de modèle qui insère un nombre complexe dans le flux de sortie.|
|[opérateur = =](../standard-library/complex-operators.md#op_eq_eq)|Vérifie l'égalité entre deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[>>d’opérateur ](../standard-library/complex-operators.md#op_gt_gt)|Fonction de modèle qui extrait un nombre complexe du flux d'entrée.|

### <a name="classes"></a>Classes

|Nom|Description|
|-|-|
|[complexe\<double>](../standard-library/complex-double.md)|Le modèle de classe explicitement spécialisé décrit un objet qui stocke une paire ordonnée d’objets, tous deux de type **`double`** , où le premier représente la partie réelle d’un nombre complexe et le second représente la partie imaginaire.|
|[complexe\<float>](../standard-library/complex-float.md)|Le modèle de classe explicitement spécialisé décrit un objet qui stocke une paire ordonnée d’objets, tous deux de type **`float`** , où le premier représente la partie réelle d’un nombre complexe et le second représente la partie imaginaire.|
|[complexe\<long double>](../standard-library/complex-long-double.md)|Le modèle de classe explicitement spécialisé décrit un objet qui stocke une paire ordonnée d’objets, tous deux de type **`long double`** , où le premier représente la partie réelle d’un nombre complexe et le second représente la partie imaginaire.|
|[complexe](../standard-library/complex-class.md)|Le modèle de classe décrit un objet utilisé pour représenter le système de nombres complexes et effectuer des opérations arithmétiques complexes.|

### <a name="literals"></a>Littéraux

L' \<complex> en-tête définit les [littéraux définis par l’utilisateur](../cpp/user-defined-literals-cpp.md) suivants qui créent un nombre complexe avec la partie réelle égale à zéro et la partie imaginaire étant la valeur du paramètre d’entrée.

|Déclaration|Description|
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br />`constexpr complex<long double> operator""il(unsigned long long d)`|Retourne : `complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br />`constexpr complex<double> operator""i(unsigned long long d)`|Retourne : `complex<double>{0.0, static_cast<double>(d)}`.|
|`constexpr complex<float> operator""if(long double d)`<br />`constexpr complex<float> operator""if(unsigned long long d)`|Retourne : `complex<float>{0.0f, static_cast<float>(d)}`.|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
