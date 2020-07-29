---
title: Conversions depuis les types intégraux non signés
ms.date: 10/02/2019
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
ms.openlocfilehash: 08b88b1343f56f8d79fc39c53505b26caecfe3c4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226462"
---
# <a name="conversions-from-unsigned-integral-types"></a>Conversions depuis les types intégraux non signés

Lorsqu’un entier non signé est converti en un type entier ou à virgule flottante, si la valeur d’origine est représentable dans le type de résultat, la valeur est inchangée.

Lors de la conversion d’un entier non signé en entier de plus grande taille, la valeur est étendue à zéro. Lors de la conversion en un entier de plus petite taille, les bits de poids fort sont tronqués. Le résultat est interprété à l’aide du type de résultat, comme indiqué dans cet exemple.

```C
unsigned k = 65533;
short j;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

Lors de la conversion d’un entier non signé en type à virgule flottante, si la valeur d’origine ne peut pas être représentée exactement dans le type de résultat, le résultat est la valeur représentable supérieure ou inférieure suivante.

Consultez [stockage des types de base](../c-language/storage-of-basic-types.md) pour plus d’informations sur les tailles des types intégraux et à virgule flottante.

**Spécifique à Microsoft**

Dans le compilateur Microsoft, **`unsigned`** (ou **`unsigned int`** ) et **`unsigned long`** sont des types distincts, mais équivalents. La conversion d’une valeur s’effectue **`unsigned int`** de la même façon que pour la conversion d’un **`unsigned long`** .

**FIN spécifique à Microsoft**

Le tableau suivant répertorie les conversions de types intégraux non signés.

## <a name="table-of-conversions-from-unsigned-integral-types"></a>Tableau des conversions des types intégraux non signés

|À partir|À|Méthode|
|----------|--------|------------|
|**`unsigned char`**|**`char`**|Conserver le modèle binaire. Le bit de poids fort devient un bit de signe|
|**`unsigned char`**|**`short`**|Extension zéro|
|**`unsigned char`**|**`long`**|Extension zéro|
|**`unsigned char`**|**`long long`**|Extension zéro|
|**`unsigned char`**|**`unsigned short`**|Extension zéro|
|**`unsigned char`**|**`unsigned long`**|Extension zéro|
|**`unsigned char`**|**`unsigned long long`**|Extension zéro|
|**`unsigned char`**|**`float`**|Convertir en **`long`** ; convertir **`long`** en**`float`**|
|**`unsigned char`**|**`double`**|Convertir en **`long`** ; convertir **`long`** en**`double`**|
|**`unsigned char`**|**`long double`**|Convertir en **`long`** ; convertir **`long`** en**`double`**|
|**`unsigned short`**|**`char`**|Conserver l'octet de poids faible|
|**`unsigned short`**|**`short`**|Conserver le modèle binaire. Le bit de poids fort devient un bit de signe|
|**`unsigned short`**|**`long`**|Extension zéro|
|**`unsigned short`**|**`long long`**|Extension zéro|
|**`unsigned short`**|**`unsigned char`**|Conserver l'octet de poids faible|
|**`unsigned short`**|**`unsigned long`**|Extension zéro|
|**`unsigned short`**|**`unsigned long long`**|Extension zéro|
|**`unsigned short`**|**`float`**|Convertir en **`long`** ; convertir **`long`** en**`float`**|
|**`unsigned short`**|**`double`**|Convertir en **`long`** ; convertir **`long`** en**`double`**|
|**`unsigned short`**|**`long double`**|Convertir en **`long`** ; convertir **`long`** en**`double`**|
|**`unsigned long`**|**`char`**|Conserver l'octet de poids faible|
|**`unsigned long`**|**`short`**|Conserver le mot de poids faible|
|**`unsigned long`**|**`long`**|Conserver le modèle binaire. Le bit de poids fort devient un bit de signe|
|**`unsigned long`**|**`long long`**|Extension zéro|
|**`unsigned long`**|**`unsigned char`**|Conserver l'octet de poids faible|
|**`unsigned long`**|**`unsigned short`**|Conserver le mot de poids faible|
|**`unsigned long`**|**`unsigned long long`**|Extension zéro|
|**`unsigned long`**|**`float`**|Convertir en **`long`** ; convertir **`long`** en**`float`**|
|**`unsigned long`**|**`double`**|Convertir directement en**`double`**|
|**`unsigned long`**|**`long double`**|Convertir en **`long`** ; convertir **`long`** en**`double`**|
|**`unsigned long long`**|**`char`**|Conserver l'octet de poids faible|
|**`unsigned long long`**|**`short`**|Conserver le mot de poids faible|
|**`unsigned long long`**|**`long`**|Conserver le DWORD de poids faible|
|**`unsigned long long`**|**`long long`**|Conserver le modèle binaire. Le bit de poids fort devient un bit de signe|
|**`unsigned long long`**|**`unsigned char`**|Conserver l'octet de poids faible|
|**`unsigned long long`**|**`unsigned short`**|Conserver le mot de poids faible|
|**`unsigned long long`**|**`unsigned long`**|Conserver le DWORD de poids faible|
|**`unsigned long long`**|**`float`**|Convertir en **`long`** ; convertir **`long`** en**`float`**|
|**`unsigned long long`**|**`double`**|Convertir directement en**`double`**|
|**`unsigned long long`**|**`long double`**|Convertir en **`long`** ; convertir **`long`** en**`double`**|

## <a name="see-also"></a>Voir aussi

[Conversions d’affectation](../c-language/assignment-conversions.md)
