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
ms.openlocfilehash: bfbca4ae87d84286b94120eaf24de928ae75f3c9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200320"
---
# <a name="data-type-specifiers-and-equivalents"></a>Spécificateurs de type de données et équivalents

Ce livre utilise généralement les formes des spécificateurs de type listés dans le tableau ci-dessous plutôt que les formes longues, et il suppose que le **`char`** type est signé par défaut. Par conséquent, tout au long de cet ouvrage, **`char`** est équivalent à **`signed char`** .

## <a name="type-specifiers-and-equivalents"></a>Spécificateurs de type et équivalents

|Spécificateur de type|Équivalent(s)|
|--------------------|---------------------|
|**`signed char`** 1,0|**`char`**|
|**`signed int`**|**`signed`**, **`int`**|
|**`signed short int`**|**`short`**, **`signed short`**|
|**`signed long int`**|**`long`**, **`signed long`**|
|**`unsigned char`**|—|
|**`unsigned int`**|**`unsigned`**|
|**`unsigned short int`**|**`unsigned short`**|
|**`unsigned long int`**|**`unsigned long`**|
|**`float`**|—|
|**`long double`** 2|—|

1 quand vous rendez le **`char`** type non signé par défaut (en spécifiant l' **`/J`** option du compilateur), vous ne pouvez pas abréger **`signed char`** en tant que **`char`** .

2 dans les systèmes d’exploitation 32 bits et 64 bits, le compilateur Microsoft C mappe **`long double`** en type **`double`** .

**Spécifique à Microsoft**

Vous pouvez spécifier l' **`/J`** option de compilateur pour remplacer le type par défaut par **`char`** **`signed char`** **`unsigned char`** . Lorsque cette option est activée, **`char`** signifie comme **`unsigned char`** et vous devez utiliser le **`signed`** mot clé pour déclarer une valeur de caractère signée. Si une **`char`** valeur est déclarée explicitement **`signed`** , l' **`/J`** option ne l’affecte pas, et la valeur est étendue par un signe lorsqu’elle est élargie à un **`int`** type. Le **`char`** type est étendu par zéro lorsqu’il est élargi au **`int`** type.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Spécificateurs de type C](../c-language/c-type-specifiers.md)
