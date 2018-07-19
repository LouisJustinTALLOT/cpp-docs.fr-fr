---
title: '&lt;complex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <complex>
- std::<complex>
dev_langs:
- C++
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e6a8364c6f0491344eef7faf381d701944f66d9
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965667"
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

Définit la classe de modèle de conteneur `complex` et ses modèles de prise en charge.

## <a name="syntax"></a>Syntaxe

```cpp
#include <complex>
```

## <a name="remarks"></a>Notes

Un nombre complexe est une paire ordonnée de nombres réels. En termes purement géométriques, le plan complexe est le plan réel à deux dimensions. Les qualités spéciales du plan complexe qui le distinguent du plan réel sont dues au fait qu'il a une structure algébrique supplémentaire. Cette structure algébrique a deux opérations fondamentales :

- Addition, définie comme (*un*, *b*) + (*c*, *d*) = (*un* + *c* , *b* + *d*)

- Multiplication, définie comme (*un*, *b*) \* (*c*, *d*) = (*ac*  -  *bd*, *ad* + *bc*)

L'ensemble de nombres complexes avec les opérations d'addition complexe et de multiplication complexe est un domaine au sens algébrique standard :

- Les opérations d'addition et multiplication sont commutatives et associatives, et la multiplication se distribue sur l'addition exactement comme elle le fait avec l'addition et la multiplication de réels sur le domaine des nombres réels.

- Nombre complexe (0, 0) est l’identité additive et (1, 0) est l’identité multiplicative.

- L’inverse additif d’un nombre complexe (*un*, *b*) est (-*un*, -*b*) et l’inverse multiplicatif pour tous les nombres complexes à l’exception (0, 0) est

   (*un*/ (*un*<sup>2</sup> + *b*<sup>2</sup>), -*b*/ (*un*<sup>2</sup> + *b*<sup>2</sup>))

En représentant un nombre complexe *z* = (*un*, *b*) sous la forme *z* = *un*  +  *bi*, où *je*<sup>2</sup> = -1, les règles pour l’algèbre de l’ensemble de nombres réels peut être appliquée à l’ensemble de nombres complexes et à leurs composants. Exemple :

   (1 + 2*je*) \* (2 + 3*je*)  
   = 1 \* (2 + 3*je*) + 2*je* \* (2 + 3*je*)  
   = (2 + 3*je*) + (4*je* + 6*je*<sup>2</sup>)  
   = (2 - 6) + (3 + 4)*je*  
   = -4 + 7*je*

Le système des nombres complexes est un domaine, mais il n'est pas un domaine ordonné. Il n’existe aucun classement de nombres complexes qu’il existe pour le champ de nombres réels et ses sous-ensembles, donc les inégalités ne peuvent pas être appliquées aux nombres complexes, tels qu’ils sont en nombres réels.

Il existe trois formes courantes de représentation d’un nombre complexe *z* :

- Cartésienne : *z* = *un* + *bi*

- Polaire : *z* = *r* (cos *p* + *je* sin *p*)

- Exponentielle : *z* = *r* \* *e*<sup>*ip*</sup>

Les termes utilisés dans ces représentations standard d'un nombre complexe s'entendent comme suit :

- Le composant cartésien réel ou la partie réelle *a*.

- Le composant cartésien imaginaire ou la partie imaginaire *b*.

- Le module ou la valeur absolue d’un nombre complexe *r*.

- L’argument ou angle de phase *p* en radians.

Sauf indication contraire, les fonctions qui peuvent retourner plusieurs valeurs sont requises pour retourner une valeur principale pour leurs arguments supérieur à - π et inférieur à ou égal à + π laissez-les unique table. Tous les angles doivent être exprimées en radians, où il n’y 2π radians (360 degrés) dans un cercle.

### <a name="functions"></a>Fonctions

|Fonction|Description|
|-|-|
|[abs](../standard-library/complex-functions.md#abs)|Calcule le module d'un nombre complexe.|
|[arg](../standard-library/complex-functions.md#arg)|Extrait l’argument d’un nombre complexe.|
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
|[real](../standard-library/complex-functions.md#real)|Extrait le composant réel d'un nombre complexe.|
|[sin](../standard-library/complex-functions.md#sin)|Retourne le sinus d'un nombre complexe.|
|[sinh](../standard-library/complex-functions.md#sinh)|Retourne le sinus hyperbolique d'un nombre complexe.|
|[sqrt](../standard-library/complex-functions.md#sqrt)|Retourne la racine carrée d'un nombre complexe.|
|[tan](../standard-library/complex-functions.md#tan)|Retourne la tangente d'un nombre complexe.|
|[tanh](../standard-library/complex-functions.md#tanh)|Retourne la tangente hyperbolique d'un nombre complexe.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator!=](../standard-library/complex-operators.md#op_neq)|Vérifie l'inégalité entre deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[operator*](../standard-library/complex-operators.md#op_star)|Multiplie deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[operator+](../standard-library/complex-operators.md#op_add)|Additionne deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[operator-](../standard-library/complex-operators.md#operator-)|Soustrait deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[operator/](../standard-library/complex-operators.md#op_div)|Divise deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[operator<\<](../standard-library/complex-operators.md#op_lt_lt)|Fonction de modèle qui insère un nombre complexe dans le flux de sortie.|
|[operator==](../standard-library/complex-operators.md#op_eq_eq)|Vérifie l'égalité entre deux nombres complexes, l'un d'entre eux ou les deux pouvant appartenir au sous-ensemble du type pour les parties réelles et imaginaires.|
|[operator>>](../standard-library/complex-operators.md#op_gt_gt)|Fonction de modèle qui extrait un nombre complexe du flux d'entrée.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[complex\<double>](../standard-library/complex-double.md)|La classe de modèle explicitement spécialisée décrit un objet qui stocke une paire ordonnée d’objets, tous deux de type **double**, où le premier représente la partie réelle d’un nombre complexe et le second représente la partie imaginaire.|
|[complex\<float>](../standard-library/complex-float.md)|La classe de modèle explicitement spécialisée décrit un objet qui stocke une paire ordonnée d’objets, tous deux de type **float**, où le premier représente la partie réelle d’un nombre complexe et le second représente la partie imaginaire.|
|[complex\<long double>](../standard-library/complex-long-double.md)|La classe de modèle explicitement spécialisée décrit un objet qui stocke une paire ordonnée d’objets, tous deux de type **long double**, où le premier représente la partie réelle d’un nombre complexe et le second représente la partie imaginaire.|
|[complex](../standard-library/complex-class.md)|La classe de modèle décrit un objet utilisé pour représenter le système des nombres complexes et pour effectuer des opérations arithmétiques complexes.|

### <a name="literals"></a>Littéraux

L’en-tête \<complex> définit les [littéraux définis par l’utilisateur](../cpp/user-defined-literals-cpp.md) suivants, qui créent un nombre complexe avec la partie réelle équivalant à zéro et la partie imaginaire étant la valeur du paramètre d’entrée.

|||
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br /><br /> `constexpr complex<long double> operator""il(unsigned long long d)`|Retourne : `complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br /><br /> `constexpr complex<double> operator""i(unsigned long long d)`|Retourne : `complex<double>{0.0, static_cast<double>(d)}`.|
|`constexpr complex<float> operator""if(long double d)`<br /><br /> `constexpr complex<float> operator""if(unsigned long long d)`|Retourne : `complex<float>{0.0f, static_cast<float>(d)}`.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
