---
title: Spécificateurs de type de données et équivalents
ms.date: 11/04/2016
helpviewer_keywords:
- type specifiers [C++], list
- widening integers
- data types [C++], equivalents
- sign-extending integral types
- zero-extending
- identifiers, data type
- data types [C++], specifiers
- simple types, names
- type names [C++], simple
ms.assetid: 0d4b515a-4f68-4786-83cf-a5d43c7cb6f3
ms.openlocfilehash: 4003d9427c160b0e1c725cdc591190bd9777b3de
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151670"
---
# <a name="data-type-specifiers-and-equivalents"></a>Spécificateurs de type de données et équivalents

Cet ouvrage utilise généralement les formes des spécificateurs de type répertoriées dans le tableau ci-dessous plutôt que les formes longues, et il suppose que le type `char` est signé par défaut. Par conséquent, dans l’ensemble de cet ouvrage, `char` est équivalent à **signed char**.

### <a name="type-specifiers-and-equivalents"></a>Spécificateurs de type et équivalents

|Spécificateur de type|Équivalent(s)|
|--------------------|---------------------|
|**signed char**1|**char**|
|**signed int**|**signed**, **int**|
|**signed short int**|**short**, **signed short**|
|**signed long int**|**long**, **signed long**|
|**unsigned char**|—|
|**unsigned int**|**unsigned**|
|**unsigned short int**|**unsigned short**|
|**unsigned long int**|**unsigned long**|
|**float**|—|
|**long double**2|—|

1   Lorsque vous spécifiez le type **char** comme étant non signé par défaut (en spécifiant l’option /J du compilateur), vous ne pouvez pas abréger **signed char** en **char**.

2   Dans les systèmes d’exploitation 32 bits et 64 bits, le compilateur Microsoft C mappe **long double** sur le type **double**.

**Section spécifique à Microsoft**

Vous pouvez spécifier l’option /J du compilateur pour modifier le type **char** par défaut de signé à non signé. Lorsque cette option est appliquée, **char** a la même signification que **unsigned char**, et vous devez utiliser le mot clé **signed** pour déclarer une valeur de caractère signée. Si une valeur **char** est déclarée explicitement comme étant signée, l’option /J ne l’affecte pas, et la valeur est étendue par un signe lorsqu’elle est élargie à un type **int**. Le type **char** est étendu par zéro lorsqu’il est élargi au type **int**.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Spécificateurs de type C](../c-language/c-type-specifiers.md)
