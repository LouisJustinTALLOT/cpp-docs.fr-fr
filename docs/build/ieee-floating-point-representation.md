---
title: Représentation à virgule flottante IEEE
ms.date: 11/04/2016
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
ms.openlocfilehash: 69686e7e1c8994b799607eebf7e50387ed688272
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825773"
---
# <a name="ieee-floating-point-representation"></a>Représentation à virgule flottante IEEE

Microsoft Visual C++ est cohérent avec les standards numériques IEEE. La norme IEEE-754 décrit les formats à virgule flottante, une méthode pour représenter des nombres réels dans le matériel. Il existe au moins cinq formats internes pour les nombres à virgule flottante qui peuvent être représentées dans le matériel ciblé par le compilateur MSVC, mais le compilateur utilise uniquement deux d'entre eux. Le *simple précision* (4 octets) et *double précision* les formats (8 octets) sont utilisés dans Visual C++. Simple précision est déclarée à l’aide du mot clé **float**. Double précision est déclarée à l’aide du mot clé **double**. La norme IEEE spécifie également *demi-précision* (2 octets) et *quadruple-précision* formats (16 octets), ainsi qu’une *double étendu-précision* (10 octets) format, certains compilateurs C et C++ implémentent en tant que le **long double** type de données. Dans le compilateur MSVC, le **long double** type de données est traité comme un type distinct, mais le type de stockage est mappé sur **double**. Il existe, toutefois, intrinsèque et prise en charge du langage assembleur pour effectuer des calculs à l’aide d’autres formats, y compris l’étendue-format double précision (10 octets), où la prise en charge par le matériel.

Les valeurs sont stockées comme suit :

|Value|Stockées en tant que|
|-----------|---------------|
|simple précision|bit de signe, exposant 8 bits, mantisse de 23 bits|
|double-precision|bit de signe, exposant de 11 bits, mantisse 52 bits|
|double-extended-precision|bit de signe, exposant de 15 bits, 64 bits mantisse|

Dans les formats simple précision et double précision, il est une valeur 1 dans la partie fractionnaire, appelée le *mantisse* (et parfois appelé le *mantisse*), qui est ne pas stocké dans mémoire, par conséquent, significands sont en fait à 24 ou 53 bits, même si seuls 23 ou 52 bits sont stockés. Le format de précision étendue double stocke réellement ce bit.

Les exposants sont tronqués de la moitié de leur valeur possible. Cela signifie que vous soustrayez cet écart de l’exposant stocké pour obtenir l’exposant réel. Si l’exposant stocké est inférieur à l’écart, il est en fait un exposant négatif.

Les exposants sont tronqués comme suit :

|Exposant|Influencés par|
|--------------|---------------|
|8 bits (simple précision)|127|
|11 bits (double précision)|1023|
|15 bits (double étendu-précision)|16383|

Ces exposants ne sont pas des puissances de 10 ; ils sont des puissances de deux. Autrement dit, les exposants 8 bits stockés peuvent varier de -127 à 127, stockées en tant que 0 à 254. La valeur 2<sup>127</sup> est à peu près équivalente à 10<sup>38</sup>, qui est la limite réelle de la simple précision.

La mantisse est stockée sous forme de fraction binaire sous la forme format 1.XXX.... Cette fraction a une valeur supérieure ou égale à 1 et inférieure à 2. Notez que les nombres réels sont toujours stockés dans *normalisées formulaire*; autrement dit, la mantisse est décalée à gauche de telle sorte que le bit de poids fort de la mantisse est toujours 1. Étant donné que ce bit est toujours 1, il est supposé (non stocké) dans les formats simple précision et double précision. La virgule binaire (non décimale) est censée pour être juste à droite de la valeur 1.

Le format, puis, pour différentes tailles est comme suit :

|Format|byte 1|byte 2|byte 3|byte 4|...|byte n|
|------------|------------|------------|------------|------------|---------|------------|
|simple précision| `SXXXXXXX`|`XMMMMMMM`|`MMMMMMMM`|`MMMMMMMM`|||
|double-precision|`SXXXXXXX`|`XXXXMMMM`|`MMMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|
|double-extended-precision|`SXXXXXXX`|`XXXXXXXX`|`1MMMMMMM`|`MMMMMMMM`|...|`MMMMMMMM`|

`S` représente le bit de signe, le `X`de sont les bits d’exposant biaisés et le `M`de sont les bits de la mantisse. Notez que le bit le plus à gauche est supposé dans les formats simple précision et double précision, mais est présent en tant que « 1 » dans l’octet 3 de l’étendue-format double précision.

Pour décaler la virgule binaire correctement, vous tout d’abord devez l’exposant et ensuite déplacez la virgule binaire vers la droite ou gauche du nombre approprié de bits.

## <a name="special-values"></a>Valeurs spéciales

Les formats à virgule flottante incluent des valeurs qui sont traités spécialement.

### <a name="zero"></a>Zéro

Zéro ne peut pas être normalisé, ce qui rend non représentable sous la forme normalisée d’une valeur simple précision ou double précision. Un modèle de bit spécial de tous les zéros représente 0. Il est également possible pour représenter - 0 en tant que zéro par le signe bit défini, mais - 0 et 0 sont toujours considérées comme égales.

### <a name="infinities"></a>Valeurs infinies

Le + ∞ et −∞ valeurs sont représentées par un exposant de tous les zéros et d’une mantisse de zéros. Infinis à la fois positives et négatives peuvent être représentés en utilisant le bit de signe.

### <a name="subnormals"></a>Subnormals

Il est possible de représenter les nombres de magnitude plus petit au plus petit nombre normalisé. Ces numéros sont appelés *subnormal* ou *denormal* numéros. Si l’exposant est tous les zéros non significatifs et la mantisse est différente de zéro, puis implicite bits de début de la mantisse est considéré comme égal à zéro, pas un. La précision des nombres subnormal tombe en panne, comme le nombre de zéros non significatifs dans la mantisse augmente.

### <a name="nan---not-a-number"></a>NaN - pas un nombre

Il est possible de représenter les valeurs qui ne sont pas un nombre réel, telles que 0 / 0, dans le format à virgule flottante IEEE. Une valeur de ce type est appelée un *NaN*. Une valeur NaN est représentée par un exposant des uns et une mantisse de zéro. Il existe deux types de valeurs NaN, *silencieux* NaN ou QNaNs, et *signalisation* NaN ou SNaNs. Quiet NaN ont un début dans la mantisse et sont généralement propagées via une expression. Ils représentent une valeur indéterminée, tel que le résultat de la division par l’infini ou la multiplication d’un nombre infini par zéro. Valeurs NaN de signalisation ont un zéro non significatif dans la mantisse. Ils sont utilisés pour les opérations qui ne sont pas valides, pour signaler une exception à virgule flottante matérielle.

## <a name="examples"></a>Exemples

Voici quelques exemples dans le format de la simple précision :

- Pour la valeur 2, le bit de signe est égal à zéro et l’exposant stocké est 128 ou 1000 0000 en binaire, c'est-à-dire 127 plus 1. La mantisse binaire stockée est (1). 000 0000 0000 0000 0000 0000, ce qui a un implicite début 1 et binaire point, par conséquent, la mantisse réelle est un.

   |Value|Formule|Représentation binaire|Hexadécimal|
   |-|-|-|-|
   |2|1 * 2<sup>1</sup>|0100 0000 0000 0000 0000 0000 0000 0000|0x40000000|

- La valeur -2. Identique à + 2, à ceci près que le bit de signe est défini. Cela est vrai pour la valeur négative de tous les nombres à virgule flottante de format IEEE.

   |Value|Formule|Représentation binaire|Hexadécimal|
   |-|-|-|-|
   |-2|-1 * 2<sup>1</sup>|1100 0000 0000 0000 0000 0000 0000 0000|0xC0000000|

- La valeur 4. Même mantisse, exposant augmente de 1 (valeur biaisée est 129, soit 100 0000 1 en binaire.

   |Value|Formule|Représentation binaire|Hexadécimal|
   |-|-|-|-|
   |4|1 * 2<sup>2</sup>|0100 0000 1000 0000 0000 0000 0000 0000|0x40800000|

- La valeur 6. Même exposant, la mantisse est supérieure de moitié — d’il (1). 100 0000 ... 0000 0000, c'est-à-dire, dans la mesure où il s’agit d’une fraction binaire, 1 1/2, car les valeurs des chiffres fractionnaires sont 1/2, 1/4, 1/8 et ainsi de suite.

   |Value|Formule|Représentation binaire|Hexadécimal|
   |-|-|-|-|
   |6|1.5 * 2<sup>2</sup>|0100 0000 1100 0000 0000 0000 0000 0000|0x40C00000|

- La valeur 1. Mantisse de même que d’autres puissances de deux, l’exposant tronqué est une inférieures à deux 127, soit 011 1111 1 en binaire.

   |Value|Formule|Représentation binaire|Hexadécimal|
   |-|-|-|-|
   |1|1 * 2<sup>0</sup>|0011 1111 1000 0000 0000 0000 0000 0000|0x3F800000|

- La valeur 0,75. L’exposant tronqué est 126 011 1111 0 en représentation binaire et la mantisse est (1). 100 0000 ... 0000 0000, 1 1/2.

   |Value|Formule|Représentation binaire|Hexadécimal|
   |-|-|-|-|
   |0.75|1.5 * 2<sup>-1</sup>|0011 1111 0100 0000 0000 0000 0000 0000|0x3F400000|

- La valeur 2.5. Exactement comme deux sauf que le bit qui représente 1/4 est défini dans la mantisse.

   |Value|Formule|Représentation binaire|Hexadécimal|
   |-|-|-|-|
   |2.5|1.25 * 2<sup>1</sup>|0100 0000 0010 0000 0000 0000 0000 0000|0x40200000|

- 1/10 est une fraction itérative en binaire. La mantisse est juste en deçà de 1.6, et l’exposant tronqué indique que 1.6 doit être divisée par 16 (il est 011 1101 1 en binaire, ce qui est 123 au format décimal). L’exposant réel est 123-127 = - 4, ce qui signifie que le facteur par lequel multiplier est de 2<sup>-4</sup> = 1/16. Notez que la mantisse stockée est arrondie dans le dernier bit — une tentative pour représenter le nombre non représentable aussi précisément que possible. (La raison pour laquelle ce 1/10 et 1/100 sont pas exactement est représentable dans le fichier binaire est similaire à la raison que 1/3 est pas exactement qui peut être représenté au format décimal.)

   |Value|Formule|Représentation binaire|Hexadécimal|
   |-|-|-|-|
   |0.1|1.6 * 2<sup>-4</sup>|0011 1101 1100 1100 1100 1100 1100 1101|0x3DCCCCCD|

- Zéro est un cas spécial qui utilise la formule pour la valeur minimale possible qui peut être représentée positif, c'est-à-dire tous les zéros non significatifs.

   |Value|Formule|Représentation binaire|Hexadécimal|
   |-|-|-|-|
   |0|1 * 2<sup>-128</sup>|0000 0000 0000 0000 0000 0000 0000 0000|0x00000000|

## <a name="see-also"></a>Voir aussi

[Pourquoi les nombres à virgule flottante peuvent manquer de précision](why-floating-point-numbers-may-lose-precision.md)