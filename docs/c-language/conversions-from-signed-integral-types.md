---
title: Conversions depuis des types intégraux signés
ms.date: 10/02/2019
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
ms.openlocfilehash: d41d2fd205a87f9f2be2179ffd8e38256a96e4f7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226475"
---
# <a name="conversions-from-signed-integral-types"></a>Conversions depuis des types intégraux signés

Lorsqu’un entier signé est converti en un entier ou un type à virgule flottante, si la valeur d’origine est représentable dans le type de résultat, la valeur est inchangée.

Lorsqu’un entier signé est converti en un entier de plus grande taille, la valeur est de type signe étendu. En cas de conversion en un entier de plus petite taille, les bits de poids fort sont tronqués. Le résultat est interprété à l’aide du type de résultat, comme indiqué dans cet exemple :

```C
int i = -3;
unsigned short u;

u = i;
printf_s( "%hu\n", u );  // Prints 65533
```

Lors de la conversion d’un entier signé en type à virgule flottante, si la valeur d’origine n’est pas représentable exactement dans le type de résultat, le résultat est la valeur représentable supérieure ou inférieure suivante.

Pour plus d’informations sur les tailles des types intégraux et à virgule flottante, consultez [stockage des types de base](../c-language/storage-of-basic-types.md).

Le tableau suivant répertorie les conversions de types intégraux signés. Il suppose que le **`char`** type est signé par défaut. Si vous utilisez une option au moment de la compilation pour modifier la valeur par défaut pour le **`char`** type en non signé, les conversions données dans le tableau [conversions de types intégraux non signés](../c-language/conversions-from-unsigned-integral-types.md) pour le **`unsigned char`** type s’appliquent, au lieu des conversions dans ce tableau.

**Spécifique à Microsoft**

Dans le compilateur Microsoft, **`int`** et **`long`** sont distincts, mais des types équivalents. La conversion d’une valeur s’effectue **`int`** de la même façon que pour la conversion d’un **`long`** .

**FIN spécifique à Microsoft**

## <a name="table-of-conversions-from-signed-integral-types"></a>Tableau des conversions des types intégraux signés

|À partir|À|Méthode|
|----------|--------|------------|
|**`char`**<sup>1,0</sup>|**`short`**|Étendre le signe|
|**`char`**|**`long`**|Étendre le signe|
|**`char`**|**`long long`**|Étendre le signe|
|**`char`**|**`unsigned char`**|Conserver le modèle. Le bit de poids fort perd sa fonction de bit de signe|
|**`char`**|**`unsigned short`**|Étendre la signature à **`short`** ; convertir **`short`** en**`unsigned short`**|
|**`char`**|**`unsigned long`**|Étendre la signature à **`long`** ; convertir **`long`** en**`unsigned long`**|
|**`char`**|**`unsigned long long`**|Étendre la signature à **`long long`** ; convertir **`long long`** en**`unsigned long long`**|
|**`char`**|**`float`**|Étendre la signature à **`long`** ; convertir **`long`** en**`float`**|
|**`char`**|**`double`**|Étendre la signature à **`long`** ; convertir **`long`** en**`double`**|
|**`char`**|**`long double`**|Étendre la signature à **`long`** ; convertir **`long`** en**`double`**|
|**`short`**|**`char`**|Conserver l'octet de poids faible|
|**`short`**|**`long`**|Étendre le signe|
|**`short`**|**`long long`**|Étendre le signe|
|**`short`**|**`unsigned char`**|Conserver l'octet de poids faible|
|**`short`**|**`unsigned short`**|Conserver le modèle binaire. Le bit de poids fort perd sa fonction de bit de signe|
|**`short`**|**`unsigned long`**|Étendre la signature à **`long`** ; convertir **`long`** en**`unsigned long`**|
|**`short`**|**`unsigned long long`**|Étendre la signature à **`long long`** ; convertir **`long long`** en**`unsigned long long`**|
|**`short`**|**`float`**|Étendre la signature à **`long`** ; convertir **`long`** en**`float`**|
|**`short`**|**`double`**|Étendre la signature à **`long`** ; convertir **`long`** en**`double`**|
|**`short`**|**`long double`**|Étendre la signature à **`long`** ; convertir **`long`** en**`double`**|
|**`long`**|**`char`**|Conserver l'octet de poids faible|
|**`long`**|**`short`**|Conserver le mot de poids faible|
|**`long`**|**`long long`**|Étendre le signe|
|**`long`**|**`unsigned char`**|Conserver l'octet de poids faible|
|**`long`**|**`unsigned short`**|Conserver le mot de poids faible|
|**`long`**|**`unsigned long`**|Conserver le modèle binaire. Le bit de poids fort perd sa fonction de bit de signe|
|**`long`**|**`unsigned long long`**|Étendre la signature à **`long long`** ; convertir **`long long`** en**`unsigned long long`**|
|**`long`**|**`float`**|Représente comme **`float`** . Si **`long`** ne peut pas être représenté exactement, certaines précisions sont perdues.|
|**`long`**|**`double`**|Représente comme **`double`** . Si **`long`** ne peut pas être représenté exactement comme un **`double`** , une certaine précision est perdue.|
|**`long`**|**`long double`**|Représente comme **`double`** . Si **`long`** ne peut pas être représenté exactement comme un **`double`** , une certaine précision est perdue.|
|**`long long`**|**`char`**|Conserver l'octet de poids faible|
|**`long long`**|**`short`**|Conserver le mot de poids faible|
|**`long long`**|**`long`**|Conserver le DWORD de poids faible|
|**`long long`**|**`unsigned char`**|Conserver l'octet de poids faible|
|**`long long`**|**`unsigned short`**|Conserver le mot de poids faible|
|**`long long`**|**`unsigned long`**|Conserver le DWORD de poids faible|
|**`long long`**|**`unsigned long long`**|Conserver le modèle binaire. Le bit de poids fort perd sa fonction de bit de signe|
|**`long long`**|**`float`**|Représente comme **`float`** . Si **`long long`** ne peut pas être représenté exactement, certaines précisions sont perdues.|
|**`long long`**|**`double`**|Représente comme **`double`** . Si **`long long`** ne peut pas être représenté exactement comme un **`double`** , une certaine précision est perdue.|
|**`long long`**|**`long double`**|Représente comme **`double`** . Si **`long long`** ne peut pas être représenté exactement comme un **`double`** , une certaine précision est perdue.|

<sup>1</sup> toutes les **`char`** entrées partent du principe que le **`char`** type est signé par défaut.

## <a name="see-also"></a>Voir aussi

[Conversions d’affectation](../c-language/assignment-conversions.md)
