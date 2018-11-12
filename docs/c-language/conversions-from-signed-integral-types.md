---
title: Conversions depuis les types intégraux signés
ms.date: 11/04/2016
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
ms.openlocfilehash: aec00ce21887759b2016523ff4044eb8389131fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431718"
---
# <a name="conversions-from-signed-integral-types"></a>Conversions depuis les types intégraux signés

Lorsqu'un entier signé est converti en entier non signé de taille égale ou supérieure et que la valeur de l'entier signé n'est pas négative, la valeur reste inchangée. La conversion s'effectue en étendant le signe de l'entier signé. Un entier signé est converti en entier signé plus court en tronquant les bits de poids fort. Le résultat est interprété comme une valeur non signée, comme illustré dans cet exemple.

```C
int i = -3;
unsigned short u;

u = i;
printf_s( "%hu\n", u );  // Prints 65533
```

Aucune information n’est perdue lorsqu’un entier signé est converti en valeur flottante, à l’exception de précisions qui peuvent être perdues lorsqu’une valeur **long int** ou **unsigned long int** est convertie en valeur **float**.

Le tableau suivant répertorie les conversions de types intégraux signés. Ce tableau suppose que le type **char** est signé par défaut. Si vous utilisez une option au moment de la compilation pour modifier la valeur par défaut du type **char** par unsigned, les conversions données dans le tableau [Conversions de types intégraux non signés](../c-language/conversions-from-unsigned-integral-types.md) pour le type **unsigned char** s’appliquent, au lieu des conversions du tableau « Conversions de types intégraux signés ».

### <a name="conversions-from-signed-integral-types"></a>Conversions depuis les types intégraux signés

|From|À|Méthode|
|----------|--------|------------|
|**char**1|**short**|Étendre le signe|
|**char**|**long**|Étendre le signe|
|**char**|**unsigned char**|Conserver le modèle. Le bit de poids fort perd sa fonction de bit de signe|
|**char**|**unsigned short**|Étendre le signe à **short**. Convertir **short** en **unsigned short**|
|**char**|**unsigned long**|Étendre le signe à **long**. Convertir **long** en **unsigned long**|
|**char**|**float**|Étendre le signe à **long**. Convertir **long** en **float**|
|**char**|**double**|Étendre le signe à **long**. Convertir **long** en **double**|
|**char**|**long double**|Étendre le signe à **long**. Convertir **long** en **double**|
|**short**|**char**|Conserver l'octet de poids faible|
|**short**|**long**|Étendre le signe|
|**short**|**unsigned char**|Conserver l'octet de poids faible|
|**short**|**unsigned short**|Conserver le modèle binaire. Le bit de poids fort perd sa fonction de bit de signe|
|**short**|**unsigned long**|Étendre le signe à **long**. Convertir **long** en **unsigned long**|
|**short**|**float**|Étendre le signe à **long**. Convertir **long** en **float**|
|**short**|**double**|Étendre le signe à **long**. Convertir **long** en **double**|
|**short**|**long double**|Étendre le signe à **long**. Convertir **long** en **double**|
|**long**|**char**|Conserver l'octet de poids faible|
|**long**|**short**|Conserver le mot de poids faible|
|**long**|**unsigned char**|Conserver l'octet de poids faible|
|**long**|**unsigned short**|Conserver le mot de poids faible|
|**long**|**unsigned long**|Conserver le modèle binaire. Le bit de poids fort perd sa fonction de bit de signe|
|**long**|**float**|Représenter comme **float**. Si **long** ne peut pas être représenté exactement, certaines précisions sont perdues.|
|**long**|**double**|Représenter comme **double**. Si **long** ne peut pas être représenté exactement comme **double**, certaines précisions sont perdues.|
|**long**|**long double**|Représenter comme **double**. Si **long** ne peut pas être représenté exactement comme **double**, certaines précisions sont perdues.|

1. Toutes les entrées **char** supposent que le type **char** est signé par défaut.

**Section spécifique à Microsoft**

Pour le compilateur Microsoft 32 bits C, un entier est équivalent à un **long**. La procédure de conversion d’une valeur **int** est identique à celle de **long**.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Conversions d’assignation](../c-language/assignment-conversions.md)