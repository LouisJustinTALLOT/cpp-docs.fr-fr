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
ms.openlocfilehash: 79608b5ca4335ee3c30bdab27e7efade5b7e2f54
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998722"
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

Le tableau suivant répertorie les conversions de types intégraux signés. Il suppose que le type **char** est signé par défaut. Si vous utilisez une option au moment de la compilation pour modifier la valeur par défaut du type **char** en non signé, les conversions données dans le tableau conversions [de types intégraux non signés](../c-language/conversions-from-unsigned-integral-types.md) pour le type **unsigned char** s’appliquent, au lieu des conversions dans ce tableau.

**Section spécifique à Microsoft**

Dans le compilateur Microsoft, les types **int** et **long** sont distincts, mais équivalents. La conversion d’une valeur **int** se déroule de la même façon que la conversion d’une valeur **long**.

**FIN de la section spécifique à Microsoft**

## <a name="table-of-conversions-from-signed-integral-types"></a>Tableau des conversions des types intégraux signés

|From|À|Méthode|
|----------|--------|------------|
|**caractère**<sup>1</sup>|**short**|Étendre le signe|
|**char**|**long**|Étendre le signe|
|**char**|**long long**|Étendre le signe|
|**char**|**unsigned char**|Conserver le modèle. Le bit de poids fort perd sa fonction de bit de signe|
|**char**|**unsigned short**|Étendre le signe à **short**. Convertir **short** en **unsigned short**|
|**char**|**unsigned long**|Étendre le signe à **long**. Convertir **long** en **unsigned long**|
|**char**|**long long non signé**|Étendre le signe à **long long**; convertir **long long** en **unsigned long** long|
|**char**|**float**|Étendre le signe à **long**. Convertir **long** en **float**|
|**char**|**double**|Étendre le signe à **long**. Convertir **long** en **double**|
|**char**|**long double**|Étendre le signe à **long**. Convertir **long** en **double**|
|**short**|**char**|Conserver l'octet de poids faible|
|**short**|**long**|Étendre le signe|
|**short**|**long long**|Étendre le signe|
|**short**|**unsigned char**|Conserver l'octet de poids faible|
|**short**|**unsigned short**|Conserver le modèle binaire. Le bit de poids fort perd sa fonction de bit de signe|
|**short**|**unsigned long**|Étendre le signe à **long**. Convertir **long** en **unsigned long**|
|**short**|**long long non signé**|Étendre le signe à **long long**; convertir **long long** en **unsigned long** long|
|**short**|**float**|Étendre le signe à **long**. Convertir **long** en **float**|
|**short**|**double**|Étendre le signe à **long**. Convertir **long** en **double**|
|**short**|**long double**|Étendre le signe à **long**. Convertir **long** en **double**|
|**long**|**char**|Conserver l'octet de poids faible|
|**long**|**short**|Conserver le mot de poids faible|
|**long**|**long long**|Étendre le signe|
|**long**|**unsigned char**|Conserver l'octet de poids faible|
|**long**|**unsigned short**|Conserver le mot de poids faible|
|**long**|**unsigned long**|Conserver le modèle binaire. Le bit de poids fort perd sa fonction de bit de signe|
|**long**|**long long non signé**|Étendre le signe à **long long**; convertir **long long** en **unsigned long** long|
|**long**|**float**|Représenter comme **float**. Si **long** ne peut pas être représenté exactement, certaines précisions sont perdues.|
|**long**|**double**|Représenter comme **double**. Si **long** ne peut pas être représenté exactement comme un **double**, une précision est perdue.|
|**long**|**long double**|Représenter comme **double**. Si **long** ne peut pas être représenté exactement comme un **double**, une précision est perdue.|
|**long long**|**char**|Conserver l'octet de poids faible|
|**long long**|**short**|Conserver le mot de poids faible|
|**long long**|**long**|Conserver le DWORD de poids faible|
|**long long**|**unsigned char**|Conserver l'octet de poids faible|
|**long long**|**unsigned short**|Conserver le mot de poids faible|
|**long long**|**unsigned long**|Conserver le DWORD de poids faible|
|**long long**|**long long non signé**|Conserver le modèle binaire. Le bit de poids fort perd sa fonction de bit de signe|
|**long long**|**float**|Représenter comme **float**. Si **long long** ne peut pas être représenté exactement, certaines précisions sont perdues.|
|**long long**|**double**|Représenter comme **double**. Si **long long** ne peut pas être représenté exactement comme un **double**, une précision est perdue.|
|**long long**|**long double**|Représenter comme **double**. Si **long long** ne peut pas être représenté exactement comme un **double**, une précision est perdue.|

<sup>1</sup> toutes les entrées **char** partent du principe que le type **char** est signé par défaut.

## <a name="see-also"></a>Voir aussi

[Conversions d’assignation](../c-language/assignment-conversions.md)
