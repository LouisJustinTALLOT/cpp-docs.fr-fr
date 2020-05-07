---
title: float, type
ms.date: 11/04/2016
helpviewer_keywords:
- type float
- exponent length
- float keyword [C]
- mantissas, length
- floating-point numbers, float type
- ranges, floating-point types
- floating-point numbers, variables
- lengths, mantissa
- double data type, type float
- IEEE floating-point representation
- lengths, exponent
ms.assetid: 706e332b-17a0-4a30-b7d8-5d6cd372524b
ms.openlocfilehash: 61bfd094801165e0c3e41e5de6fcbfb0c5e59504
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346325"
---
# <a name="type-float"></a>float, type

Les nombres à virgule flottante utilisent le format IEEE (Institute of Electrical and Electronics Engineers). Les valeurs de précision simple de type float possèdent 4 octets, comprenant un bit de signe, un exposant binaire 8 bits avec écart de 127 et une mantisse de 23 bits. La mantisse représente un nombre entre 1,0 et 2,0. Étant donné que le bit de poids fort de la mantisse est toujours 1, il n'est pas stocké dans le nombre. Cette présentation donne une plage d’environ 3,4E-38 à 3,4E+38 pour le type float.

Vous pouvez déclarer des variables comme float ou double, selon les besoins de votre application. Les principales différences entre les deux types sont l'importance qu'elles peuvent représenter, le stockage qu'elles nécessitent et leur plage. Le tableau suivant montre la relation entre l'importance et les exigences en matière de stockage.

### <a name="floating-point-types"></a>Types virgule flottante

|Type|Chiffres significatifs|Nombre d'octets|
|----------|------------------------|---------------------|
|float|6 - 7|4|
|double|15 - 16|8|

Les variables à virgule flottante sont représentées par une mantisse, qui contient la valeur du nombre et un exposant qui contient l'amplitude du nombre.

Le tableau suivant indique le nombre de bits alloués à la mantisse et l'exposant pour chaque type à virgule flottante. Le bit le plus significatif de tous les float ou double est toujours le bit de signe. S'il s'agit de 1, le nombre est considéré comme négatif ; sinon, il est considéré comme positif.

### <a name="lengths-of-exponents-and-mantissas"></a>Longueurs des exposants et des mantisses

|Type|Longueur des exposants|Longueur des mantisses|
|----------|---------------------|---------------------|
|float|8 bits|23 bits|
|double|11 bits|52 bits|

Étant donné que les exposants sont stockés dans un formulaire non signé, l'exposant est tronqué de la moitié de sa valeur possible. Pour le type float, l'écart est de 127 ; pour le type double, il est de 1023. Vous pouvez calculer la valeur d'exposant réelle en soustrayant la valeur d'écart de la valeur d'exposant.

La mantisse est stockée sous forme de fraction binaire supérieure ou égale à 1 et inférieure à 2. Pour les types float et double, la mantisse comporte une valeur 1 implicite dans la position de bit le plus significatif. La longueur réelle des mantisses est donc 24 et 53, respectivement, même si le bit le plus significatif n'est jamais stocké en mémoire.

Au lieu d'utiliser la méthode de stockage qui vient d'être décrite, le package à virgule flottante peut stocker des nombres à virgule flottante binaires comme nombres dénormalisés. Des « nombres dénormalisés » sont des nombres à virgule flottante différents de zéro avec des valeurs d'exposant réservées dans lesquelles le bit le plus significatif de la mantisse est 0. En utilisant le format dénormalisé, la plage d'un nombre à virgule flottante peut être étendue, au détriment de la précision. Vous ne pouvez pas contrôler si un nombre à virgule flottante est représenté au format normal ou dénormalisé ; le package à virgule flottante détermine la représentation. Le package à virgule flottante n'utilise jamais le format dénormalisé, sauf si l'exposant devient inférieur au minimum qu'il est possible de représenter au format normal.

Le tableau suivant affiche les valeurs minimales et maximales que vous pouvez stocker dans les variables de chaque type à virgule flottante. Les valeurs répertoriées dans ce tableau s'appliquent uniquement aux nombres à virgule flottante normalisés. Les nombres à virgule flottante dénormalisés ont une valeur minimale inférieure. Notez que les numéros conservés dans les registres 80*x*87 sont toujours représentés au format normalisé 80 bits. Seuls les nombres stockés dans des variables à virgule flottante 32 bits ou 64 bits peuvent être représentés au format dénormalisé (variables de type float et de type long).

### <a name="range-of-floating-point-types"></a>Plage des types à virgule flottante

|Type|Valeur minimale|Valeur maximale|
|----------|-------------------|-------------------|
|float|1,175494351 E - 38|3.402823466 E + 38|
|double|2,2250738585072014 E - 308|1,7976931348623158 E + 308|

Si la précision est moins importante que le stockage, vous pouvez envisager d'utiliser le type float pour les variables à virgule flottante. Inversement, si la précision est le critère le plus important, utilisez le type double.

Les variables à virgule flottante peuvent être promues à un type dont la signification est supérieure (du type float au type double). Cette promotion se produit généralement lorsque vous effectuez des opérations arithmétiques sur des variables à virgule flottante. Ces opérations arithmétiques sont toujours effectuées à un degré de précision aussi élevé que la variable ayant le degré de précision le plus élevé. Considérons par exemple les déclarations de type suivantes :

```
float f_short;
double f_long;
long double f_longer;

f_short = f_short * f_long;
```

Dans l'exemple précédent, la variable `f_short` est promue au type double et multipliée par `f_long`. Le résultat est arrondi au type float avant d'être assigné à `f_short`.

Dans l'exemple suivant (qui utilise les déclarations de l'exemple précédent), l'opération arithmétique est effectuée en précision float (32 bits) sur les variables. Le résultat est ensuite promu au type double :

```
f_longer = f_short * f_short;
```

## <a name="see-also"></a>Voir aussi

[Stockage de types de base](../c-language/storage-of-basic-types.md)
