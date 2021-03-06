---
description: 'En savoir plus sur : plages de types de données'
title: plages de types de données
ms.date: 05/28/2020
helpviewer_keywords:
- float keyword [C++]
- char keyword [C++]
- unsigned long
- __wchar_t keyword [C++]
- unsigned short int [C++]
- enum keyword [C++]
- unsigned char keyword [C++]
- integer data type [C++], data type ranges
- int data type
- data types [C++], ranges
- unsigned int [C++]
- short data type
- short int data
- signed types [C++], data type ranges
- long long keyword [C++]
- long double keyword [C++]
- double data type [C++], data type ranges
- signed short int [C++]
- unsigned short
- sized integer types
- signed int [C++]
- signed long int [C++]
- signed char keyword [C++]
- wchar_t keyword [C++]
- long keyword [C++]
- ranges [C++]
- unsigned types [C++], data type ranges
- floating-point numbers [C++]
- data type ranges
- ranges [C++], data types
- long int keyword [C++]
- unsigned long int [C++]
ms.assetid: 3691ceca-05fb-4b82-b1ae-5c4618cda91a
ms.openlocfilehash: 8d4ae1b6aae3a4dbf12180248df6000085103efe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339525"
---
# <a name="data-type-ranges"></a>plages de types de données

Les compilateurs Microsoft C++ 32 bits et 64 bits reconnaissent les types dans le tableau plus loin dans cet article.

- **`int`** (**`unsigned int`**)

- **`__int8`** (**`unsigned __int8`**)

- **`__int16`** (**`unsigned __int16`**)

- **`__int32`** (**`unsigned __int32`**)

- **`__int64`** (**`unsigned __int64`**)

- **`short`** (**`unsigned short`**)

- **`long`** (**`unsigned long`**)

- **`long long`** (**`unsigned long long`**)

Si son nom commence par deux traits de soulignement (`__`), un type de données est non standard.

Les plages spécifiées dans le tableau ci-dessous sont inclusives-inclusives.

|Nom de type|Octets|Autres noms|Plage de valeurs|
|---------------|-----------|-----------------|---------------------|
|**`int`**|4|**`signed`**|-2 147 483 648 à 2 147 483 647|
|**`unsigned int`**|4|**`unsigned`**|de 0 à 4 294 967 295|
|**`__int8`**|1|**`char`**|-128 à 127|
|**`unsigned __int8`**|1|**`unsigned char`**|0 à 255|
|**`__int16`**|2|**`short`**, **`short int`**, **`signed short int`**|-32 768 à 32 767|
|**`unsigned __int16`**|2|**`unsigned short`**, **`unsigned short int`**|0 à 65 535|
|**`__int32`**|4|**`signed`**, **`signed int`**, **`int`**|-2 147 483 648 à 2 147 483 647|
|**`unsigned __int32`**|4|**`unsigned`**, **`unsigned int`**|de 0 à 4 294 967 295|
|**`__int64`**|8|**`long long`**, **`signed long long`**|-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807|
|**`unsigned __int64`**|8|**`unsigned long long`**|de 0 à 18 446 744 073 709 551 615|
|**`bool`**|1|aucun|**`false`** ou **`true`**|
|**`char`**|1|aucun|-128 à 127 par défaut<br /><br /> 0 à 255 quand il est compilé à l’aide de [`/J`](../build/reference/j-default-char-type-is-unsigned.md)|
|**`signed char`**|1|aucun|-128 à 127|
|**`unsigned char`**|1|aucun|0 à 255|
|**`short`**|2|**`short int`**, **`signed short int`**|-32 768 à 32 767|
|**`unsigned short`**|2|**`unsigned short int`**|0 à 65 535|
|**`long`**|4|**`long int`**, **`signed long int`**|-2 147 483 648 à 2 147 483 647|
|**`unsigned long`**|4|**`unsigned long int`**|de 0 à 4 294 967 295|
|**`long long`**|8|aucun (mais équivaut à **`__int64`** )|-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807|
|**`unsigned long long`**|8|aucun (mais équivaut à **`unsigned __int64`** )|de 0 à 18 446 744 073 709 551 615|
|**`enum`**|varie|aucun| |
|**`float`**|4|aucun|3.4E +/- 38 (7 chiffres)|
|**`double`**|8|aucun|1.7E +/- 308 (15 chiffres)|
|**`long double`**|identique à **`double`**|aucun|Identique à **`double`**|
|**`wchar_t`**|2|**`__wchar_t`**|0 à 65 535|

Selon la façon dont elle est utilisée, une variable de **`__wchar_t`** désigne un type à caractères larges ou un type de caractère multioctet. Utilisez le préfixe `L` avant une constante caractère ou chaîne pour désigner la constante de type caractères larges.

**`signed`** et **`unsigned`** sont des modificateurs que vous pouvez utiliser avec tout type intégral à l’exception de **`bool`** . Notez que **`char`** , **`signed char`** et **`unsigned char`** sont trois types distincts à des fins de mécanismes tels que la surcharge et les modèles.

Les **`int`** **`unsigned int`** types et ont une taille de quatre octets. Toutefois, le code portable ne doit pas dépendre de la taille de **`int`** , car la norme du langage permet d’être spécifique à l’implémentation.

C/C++ dans Visual Studio prend également en charge les types entier dimensionnés. Pour plus d’informations, consultez [`__int8, __int16, __int32, __int64`](../cpp/int8-int16-int32-int64.md) et [limites des entiers](../cpp/integer-limits.md).

Pour plus d’informations sur les restrictions de tailles de chaque type, consultez [types intégrés](../cpp/fundamental-types-cpp.md).

La plage de types énumérés varie selon le contexte du langage et les indicateurs spécifiés du compilateur. Pour plus d'informations, consultez [Déclarations d'énumération C](../c-language/c-enumeration-declarations.md) et [Énumérations](../cpp/enumerations-cpp.md).

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Types intégrés](../cpp/fundamental-types-cpp.md)
