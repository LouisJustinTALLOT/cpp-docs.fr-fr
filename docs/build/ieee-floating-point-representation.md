---
title: Représentation à virgule flottante IEEE
ms.date: 05/06/2019
helpviewer_keywords:
- float keyword
- real*8 value
- floating-point numbers, IEEE representation
- double data type, floating-point representation
- IEEE floating point representation
- real*10 value
- long double
- real*4 value
ms.assetid: 537833e8-fe05-49fc-8169-55fd0314b195
ms.openlocfilehash: 47802a32d43824b4e568ca520c360dc7b12cbf8c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231544"
---
# <a name="ieee-floating-point-representation"></a>Représentation à virgule flottante IEEE

Microsoft C++ (MSVC) est compatible avec les normes numériques IEEE. La norme IEEE-754 décrit les formats à virgule flottante, un moyen de représenter les nombres réels dans le matériel. Il existe au moins cinq formats internes pour les nombres à virgule flottante qui sont représentables dans le matériel ciblé par le compilateur MSVC. Le compilateur utilise uniquement deux d’entre eux. Les formats à *simple précision* (4 octets) et *à double précision* (8 octets) sont utilisés dans MSVC. Une simple précision est déclarée à l’aide du mot clé **`float`** . La double précision est déclarée à l’aide du mot clé **`double`** . La norme IEEE spécifie également les formats à *demi-précision* (2 octets) et *quadruple précision* (16 octets), ainsi qu’un format *double étendu* (10 octets), que certains compilateurs C et C++ implémentent comme **`long double`** type de données. Dans le compilateur MSVC, le **`long double`** type de données est traité comme un type distinct, mais le type de stockage est mappé à **`double`** . Toutefois, il existe une prise en charge intrinsèque et du langage assembleur pour les calculs utilisant les autres formats, y compris le format double précision, qui est pris en charge par le matériel.

Les valeurs sont stockées comme suit :

|Valeur|Stocké en tant que|
|-----------|---------------|
|simple précision|bit de signe, exposant 8 bits, mantisse 23 bits|
|double précision|bit de signe, exposant 11 bits, 52 bits mantisse|

Dans les formats à simple précision et à double précision, il y a un 1 de début dans la partie fractionnaire. La partie fractionnaire est appelée *mantisse* (parfois connue sous le nom de *mantisse*). Ce 1 n’est pas stocké en mémoire, donc les significands sont en fait 24 ou 53 bits, même si un bit moins est stocké. Le format double étendu-précision stocke réellement ce bit.

Les exposants sont biaisés de la moitié de leur valeur possible. Cela signifie que vous soustrayez ce décalage de l’exposant stocké pour récupérer l’exposant réel. Si l’exposant stocké est inférieur au décalage, il s’agit en fait d’un exposant négatif.

Les exposants sont biaisés comme suit :

|Exponent|Biaisé par|
|--------------|---------------|
|8 bits (simple précision)|127|
|11 bits (double précision)|1023|

Ces exposants ne sont pas des puissances de dix ; Il s’agit de puissances de deux. Autrement dit, les exposants stockés sur 8 bits peuvent être compris entre-127 et 127, stockés entre 0 et 254. La valeur 2<sup>127</sup> est à peu près équivalente à 10<sup>38</sup>, qui est la limite réelle de simple précision.

Le mantisse est stocké sous la forme d’une fraction binaire sous la forme 1.XXX.... Cette fraction a une valeur supérieure ou égale à 1 et inférieure à 2. Les nombres réels sont toujours stockés sous une *forme normalisée*. Autrement dit, le mantisse est décalé vers la gauche de telle sorte que le bit de poids fort du mantisse est toujours 1. Étant donné que ce bit est *toujours* 1, il est supposé (non stocké) dans les formats à simple précision et à double précision. Le point binaire (non décimal) est supposé être juste à droite du premier.

Le format de la représentation à virgule flottante est le suivant :

|Format|octet 1|octet 2|octet 3|octet 4|...|octet n|
|------------|------------|------------|------------|------------|---------|------------|
|simple précision| `SXXXXXXX`|`XMMMMMMM`|`MMMMMMMM`|`MMMMMMMM`|||
|double précision|`SXXXXXXX`|`XXXXMMMM`|`MMMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|

`S`représente le bit de signe, les `X` sont les bits d’exposant biaisés, et le est `M` le mantisse bits. Le bit le plus à gauche est utilisé dans les formats à simple précision et à double précision.

Pour déplacer correctement le point binaire, vous devez d’abord supprimer l’écart entre l’exposant, puis déplacer le point binaire à droite ou à gauche du nombre de bits approprié.

## <a name="special-values"></a>Valeurs spéciales

Les formats à virgule flottante incluent des valeurs qui sont traitées de façon spéciale.

### <a name="zero"></a>Zéro

Zéro ne peut pas être normalisé, ce qui le rend non représenté sous la forme normalisée d’une valeur à simple précision ou à double précision. Un modèle binaire spécial de tous les zéros représente 0. Il est également possible de représenter-0 comme zéro avec le bit de signe défini, mais-0 et 0 sont toujours considérés comme égaux.

### <a name="infinities"></a>Infinies

Les valeurs + ∞ et − ∞ sont représentées par un exposant de tous les éléments, et un mantisse qui est constitué uniquement de zéros. Les valeurs positives et négatives sont représentées à l’aide du bit de signe.

### <a name="subnormals"></a>Sous-normales

Il est possible de représenter des nombres de plus petite amplitude que le plus petit nombre dans une forme normalisée. Ils sont appelés des nombres sous- *normaux* ou *dénormals* . Si l’exposant correspond à des zéros et que mantisse est différent de zéro, le bit de début implicite du mantisse est considéré comme zéro, pas un. La précision des nombres subnormals diminue en fonction du nombre de zéros non significatifs dans le mantisse.

### <a name="nan---not-a-number"></a>NaN-n’est pas un nombre

Il est possible de représenter des valeurs qui ne sont pas des nombres réels, telles que 0/0, dans le format à virgule flottante IEEE. Une valeur de ce genre est appelée *Nan*. Une valeur NaN est représentée par un exposant de tous les éléments et un mantisse différent de zéro. Il existe deux genres de valeurs NaN, Nan, *Quiet* , QNaNs et de *signal* Nan, ou SNaNs. Les Nan silencieux ont un de début dans le mantisse et sont propagés par le biais d’une expression. Elles représentent une valeur indéterminée, telle que le résultat de la division par l’infini, ou la multiplication d’une infini par zéro. Les valeurs NaN de signalisation ont un zéro non significatif dans le mantisse. Elles sont utilisées pour les opérations qui ne sont pas valides, pour signaler une exception matérielle à virgule flottante.

## <a name="examples"></a>Exemples

Voici quelques exemples dans un format à simple précision :

- Pour la valeur 2, le bit de signe est égal à zéro. L’exposant stocké est 128, ou 1000 0000 en binaire, ce qui est 127 plus 1. Le mantisse binaire stocké est (1.) 000 0000 0000 0000 0000 0000, qui a un point 1 et un point binaire de début implicite, donc le mantisse réel est un.

   |Valeur|Formule|Représentation binaire|Valeur hexadécimale|
   |-|-|-|-|
   |2|1 * 2<sup>1</sup>|0100 0000 0000 0000 0000 0000 0000 0000|0x40000000|

- Valeur-2. Identique à + 2, sauf que le bit de signe est défini. La même chose est vraie pour la valeur négative de tous les nombres à virgule flottante au format IEEE.

   |Valeur|Formule|Représentation binaire|Valeur hexadécimale|
   |-|-|-|-|
   |-2|-1 * 2<sup>1</sup>|1100 0000 0000 0000 0000 0000 0000 0000|0xC0000000|

- Valeur 4. Même mantisse, l’exposant augmente de 1 (la valeur biaisée est 129 ou 100 0000 1 en binaire.

   |Valeur|Formule|Représentation binaire|Valeur hexadécimale|
   |-|-|-|-|
   |4|1 * 2<sup>2</sup>|0100 0000 1000 0000 0000 0000 0000 0000|0x40800000|

- Valeur 6. Même exposant, mantisse est plus grand que la moitié. Il s’agit de (1.) 100 0000... 0000 0000, qui, puisqu’il s’agit d’une fraction binaire, est 1 1/2, car les valeurs des chiffres fractionnaires sont 1/2, 1/4, 1/8, etc.

   |Valeur|Formule|Représentation binaire|Valeur hexadécimale|
   |-|-|-|-|
   |6|1,5 * 2<sup>2</sup>|0100 0000 1100 0000 0000 0000 0000 0000|0x40C00000|

- Valeur 1. Même mantisse que d’autres puissances de deux, l’exposant biaisé est égal à un minimum de deux à 127, ou 011 1111 1 en binaire.

   |Valeur|Formule|Représentation binaire|Valeur hexadécimale|
   |-|-|-|-|
   |1|1 * 2<sup>0</sup>|0011 1111 1000 0000 0000 0000 0000 0000|0x3F800000|

- Valeur 0,75. L’exposant biaisé est 126, 011 1111 0 en binaire, et mantisse est (1.) 100 0000... 0000 0000, qui est 1 1/2.

   |Valeur|Formule|Représentation binaire|Valeur hexadécimale|
   |-|-|-|-|
   |0,75|1,5 * 2<sup>-1</sup>|0011 1111 0100 0000 0000 0000 0000 0000|0x3F400000|

- Valeur 2,5. Exactement le même que deux, sauf que le bit représentant 1/4 est défini dans mantisse.

   |Valeur|Formule|Représentation binaire|Valeur hexadécimale|
   |-|-|-|-|
   |2.5|1,25 * 2<sup>1</sup>|0100 0000 0010 0000 0000 0000 0000 0000|0x40200000|

- 1/10 est une fraction répétitive en binaire. Le mantisse est légèrement inférieur à 1,6, et l’exposant biaisé indique que 1,6 doit être divisé par 16. (011 1101 1 en binaire, soit 123 en décimal.) L’exposant réel est 123-127 =-4, ce qui signifie que le facteur par lequel multiplier est 2<sup>-4</sup> = 1/16. Le mantisse stocké est arrondi au dernier bit dans une tentative de représentation du nombre non représenté le plus précisément possible. (La raison pour laquelle 1/10 et 1/100 ne sont pas exactement représentables en binaire est semblable à la raison pour laquelle 1/3 n’est pas exactement représentable en décimal.)

   |Valeur|Formule|Représentation binaire|Valeur hexadécimale|
   |-|-|-|-|
   |0.1|1,6 * 2<sup>-4</sup>|0011 1101 1100 1100 1100 1100 1100 1101|0x3DCCCCCD|

- Zéro est un cas particulier. Elle utilise la formule pour la valeur positive minimale pouvant être représentable, qui est uniquement des zéros.

   |Valeur|Formule|Représentation binaire|Valeur hexadécimale|
   |-|-|-|-|
   |0|1 * 2<sup>-128</sup>|0000 0000 0000 0000 0000 0000 0000 0000|0x00000000|

## <a name="see-also"></a>Voir aussi

[Pourquoi les nombres à virgule flottante peuvent perdre la précision](why-floating-point-numbers-may-lose-precision.md)
