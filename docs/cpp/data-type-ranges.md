---
title: plages de types de données
ms.date: 11/04/2016
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
ms.openlocfilehash: 88fbb128d995338e5976fbb3df939524f3ef8b63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392230"
---
# <a name="data-type-ranges"></a>plages de types de données

Les compilateurs Visual C++ 32 bits et 64 bits identifient les types de la table dans la suite de cet article.

- `int` (`unsigned int`)

- `__int8` (`unsigned __int8`)

- `__int16` (`unsigned __int16`)

- `__int32` (`unsigned __int32`)

- `__int64` (`unsigned __int64`)

- `short` (`unsigned short`)

- `long` (`unsigned long`)

- `long` `long` (`unsigned long long`)

Si son nom commence par deux traits de soulignement (`__`), un type de données est non standard.

Les plages spécifiées dans le tableau ci-dessous sont inclusives-inclusives.

|Nom de type|Octets|Autres noms|Plage de valeurs|
|---------------|-----------|-----------------|---------------------|
|**int**|4|**signed**|-2,147,483,648 en 2,147,483,647|
|**unsigned int**|4|**unsigned**|de 0 à 4 294 967 295|
|**__int8**|1|**char**|-128 à 127|
|**unsigned __int8**|1|**unsigned char**|0 à 255|
|**__int16**|2|**short**, **short int**, **signed short int**|de -32 768 à 32 767|
|**unsigned __int16**|2|**unsigned short**, **entier court non signé**|0 à 65 535|
|**__int32**|4|**signed**, **signed int**, **int**|-2,147,483,648 en 2,147,483,647|
|**unsigned __int32**|4|**non signé**, **int non signé**|de 0 à 4 294 967 295|
|**__int64**|8|**long long**, **signed long long**|-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807|
|**unsigned __int64**|8|**unsigned long long**|de 0 à 18 446 744 073 709 551 615|
|**bool**|1|none|**false** ou **true**|
|**char**|1|none|-128 à 127 par défaut<br /><br /> 0 à 255 une fois compilé à l’aide de [/J](../build/reference/j-default-char-type-is-unsigned.md)|
|**char signé**|1|none|-128 à 127|
|**unsigned char**|1|none|0 à 255|
|**short**|2|**short int**, **signed short int**|de -32 768 à 32 767|
|**unsigned short**|2|**unsigned short int**|0 à 65 535|
|**long**|4|**long int**, **signed long int**|-2,147,483,648 en 2,147,483,647|
|**unsigned long**|4|**unsigned long int**|de 0 à 4 294 967 295|
|**long long**|8|Aucun (mais équivaut à **__int64**)|-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807|
|**unsigned long long**|8|Aucun (mais équivaut à **unsigned __int64**)|de 0 à 18 446 744 073 709 551 615|
|**enum**|selon le cas|none| |
|**float**|4|none|3.4E +/- 38 (7 chiffres)|
|**double**|8|none|1.7E +/- 308 (15 chiffres)|
|**long double**|identique à **double**|none|identique à **double**|
|**wchar_t**|2|**__wchar_t**|0 à 65 535|

En fonction de son utilisation, une variable de **__wchar_t** désigne un type de caractères larges ou un type de caractères multioctets. Utilisez le préfixe `L` avant une constante caractère ou chaîne pour désigner la constante de type caractères larges.

**signé** et **non signé** sont des modificateurs que vous pouvez utiliser avec n’importe quel type intégral sauf **bool**. Notez que **char**, **signé char**, et **unsigned char** sont trois types distincts dans le cadre de mécanismes tels que la surcharge et les modèles.

Le **int** et **unsigned int** types ont une taille de quatre octets. Toutefois, code portable doit dépendre pas la taille de **int** , car la norme du langage permet cette option pour être spécifique à l’implémentation.

C/C++ dans Visual Studio prend également en charge les types entier dimensionnés. Pour plus d’informations, consultez [__int8, \__int16, \__int32, \__int64](../cpp/int8-int16-int32-int64.md) et [Limites d’entier](../cpp/integer-limits.md).

Pour plus d’informations sur les restrictions de tailles de chaque type, consultez [Types fondamentaux](../cpp/fundamental-types-cpp.md).

La plage de types énumérés varie selon le contexte du langage et les indicateurs spécifiés du compilateur. Pour plus d'informations, consultez [Déclarations d'énumération C](../c-language/c-enumeration-declarations.md) et [Énumérations](../cpp/enumerations-cpp.md).

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Types fondamentaux](../cpp/fundamental-types-cpp.md)