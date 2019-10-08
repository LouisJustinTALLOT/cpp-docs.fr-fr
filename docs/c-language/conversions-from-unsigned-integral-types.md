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
ms.openlocfilehash: 3099f0113103223e392dc20560899b4a6e3ebf20
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998792"
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

**Section spécifique à Microsoft**

Dans le compilateur Microsoft, **non signé** (ou **unsigned int**) et **unsigned long** sont des types distincts, mais équivalents. La conversion d’une valeur **unsigned int** s’effectue de la même façon que la conversion d’une valeur **unsigned long**.

**FIN de la section spécifique à Microsoft**

Le tableau suivant répertorie les conversions de types intégraux non signés.

## <a name="table-of-conversions-from-unsigned-integral-types"></a>Tableau des conversions des types intégraux non signés

|From|À|Méthode|
|----------|--------|------------|
|**unsigned char**|**char**|Conserver le modèle binaire. Le bit de poids fort devient un bit de signe|
|**unsigned char**|**short**|Extension zéro|
|**unsigned char**|**long**|Extension zéro|
|**unsigned char**|**long long**|Extension zéro|
|**unsigned char**|**unsigned short**|Extension zéro|
|**unsigned char**|**unsigned long**|Extension zéro|
|**unsigned char**|**long long non signé**|Extension zéro|
|**unsigned char**|**float**|Convertir en **long**. Convertir **long** en **float**|
|**unsigned char**|**double**|Convertir en **long**. Convertir **long** en **double**|
|**unsigned char**|**long double**|Convertir en **long**. Convertir **long** en **double**|
|**unsigned short**|**char**|Conserver l'octet de poids faible|
|**unsigned short**|**short**|Conserver le modèle binaire. Le bit de poids fort devient un bit de signe|
|**unsigned short**|**long**|Extension zéro|
|**unsigned short**|**long long**|Extension zéro|
|**unsigned short**|**unsigned char**|Conserver l'octet de poids faible|
|**unsigned short**|**unsigned long**|Extension zéro|
|**unsigned short**|**long long non signé**|Extension zéro|
|**unsigned short**|**float**|Convertir en **long**. Convertir **long** en **float**|
|**unsigned short**|**double**|Convertir en **long**. Convertir **long** en **double**|
|**unsigned short**|**long double**|Convertir en **long**. Convertir **long** en **double**|
|**unsigned long**|**char**|Conserver l'octet de poids faible|
|**unsigned long**|**short**|Conserver le mot de poids faible|
|**unsigned long**|**long**|Conserver le modèle binaire. Le bit de poids fort devient un bit de signe|
|**unsigned long**|**long long**|Extension zéro|
|**unsigned long**|**unsigned char**|Conserver l'octet de poids faible|
|**unsigned long**|**unsigned short**|Conserver le mot de poids faible|
|**unsigned long**|**long long non signé**|Extension zéro|
|**unsigned long**|**float**|Convertir en **long**. Convertir **long** en **float**|
|**unsigned long**|**double**|Convertir directement en **double**|
|**unsigned long**|**long double**|Convertir en **long**. Convertir **long** en **double**|
|**long long non signé**|**char**|Conserver l'octet de poids faible|
|**long long non signé**|**short**|Conserver le mot de poids faible|
|**long long non signé**|**long**|Conserver le DWORD de poids faible|
|**long long non signé**|**long long**|Conserver le modèle binaire. Le bit de poids fort devient un bit de signe|
|**long long non signé**|**unsigned char**|Conserver l'octet de poids faible|
|**long long non signé**|**unsigned short**|Conserver le mot de poids faible|
|**long long non signé**|**unsigned long**|Conserver le DWORD de poids faible|
|**long long non signé**|**float**|Convertir en **long**. Convertir **long** en **float**|
|**long long non signé**|**double**|Convertir directement en **double**|
|**long long non signé**|**long double**|Convertir en **long**. Convertir **long** en **double**|

## <a name="see-also"></a>Voir aussi

[Conversions d’assignation](../c-language/assignment-conversions.md)
