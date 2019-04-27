---
title: Types fondamentaux (C++)
ms.date: 11/04/2016
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
- double_cpp
- float_cpp
- int_cpp
- long_cpp
- long_double_cpp
- short_cpp
- signed_cpp
- unsigned_cpp
- unsigned_int_cpp
- wchar_t_cpp
helpviewer_keywords:
- specifiers [C++], type
- float keyword [C++]
- char keyword [C++]
- __wchar_t keyword [C++]
- signed types [C++], summary of data types
- Integer data type [C++], C++ data types
- arithmetic operations [C++], types
- int data type
- unsigned types [C++], summary of data types
- short data type [C++]
- double data type [C++], summary of types
- long long keyword [C++]
- long double keyword [C++]
- unsigned types [C++]
- signed types [C++]
- void keyword [C++]
- storage [C++], basic type
- integral types, C++
- wchar_t keyword [C++]
- floating-point numbers [C++], C++ data types
- long keyword [C++]
- type specifiers [C++]
- integral types
- long keyword [C++], C++ data types
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
ms.openlocfilehash: f4af392ed559349b0e49fd26f3ecb4406a70b74b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153799"
---
# <a name="fundamental-types--c"></a>Types fondamentaux (C++)

En C++, les types fondamentaux sont divisés en trois catégories : intégral, virgule flottante et void. Les types intégraux sont capables de gérer les nombres entiers. Les types virgule flottante peuvent spécifier des valeurs pouvant avoir des parties fractionnaires.

Le type [void](../cpp/void-cpp.md) décrit un ensemble de valeurs vide. Aucune variable de type **void** peut être spécifié, il est utilisé principalement pour déclarer des fonctions qui ne retournent aucune valeur ou pour déclarer des pointeurs génériques typé ou arbitrairement des données typées. Toute expression peut être explicitement convertie ou effectuer un cast en type **void**. Toutefois, ces expressions sont limitées aux utilisations suivantes :

- Instruction d'expression. (Pour plus d'informations, consultez [Expressions](../cpp/expressions-cpp.md).)

- Opérande gauche de l'opérateur virgule. (Pour plus d'informations, consultez [Opérateur virgule](../cpp/comma-operator.md) .)

- Deuxième ou troisième opérande de l’opérateur conditionnel (`? :`). (Pour plus d'informations, consultez [Expressions avec l'opérateur conditionnel](../cpp/conditional-operator-q.md) .)

Le tableau suivant décrit les restrictions relatives aux tailles des types. Ces restrictions sont indépendantes de l'implémentation Microsoft.

### <a name="fundamental-types-of-the-c-language"></a>Types fondamentaux du langage C++

|Category|Type|Sommaire|
|--------------|----------|--------------|
|Intégral|**char**|Type **char** est un type intégral qui contient généralement les membres du jeu de caractères d’exécution de base, par défaut, il s’agit d’ASCII dans Microsoft C++.<br /><br /> Le compilateur C++ traite les variables de type **char**, **signé char**, et **unsigned char** comme ayant différents types. Variables de type **char** sont promus à **int** comme si elles sont de type **signé char** par défaut, sauf si l’option de compilation /J est utilisée. Dans ce cas, ils sont traités en tant que type **unsigned char** et sont promus à **int** sans extension de signe.|
||**bool**|Type **bool** est un type intégral qui peut avoir l’une des deux valeurs **true** ou **false**. Sa taille n'est pas spécifiée.|
||**short**|Type **short int** (ou simplement **court**) est un type intégral supérieur ou égal à la taille du type **char**et inférieur ou égal à la taille du type **int**.<br /><br /> Objets de type **court** peuvent être déclarées comme **signés short** ou **unsigned short**. **Signés short** est un synonyme de **court**.|
||**int**|Type **int** est un type intégral supérieur ou égal à la taille du type **short int**et inférieur ou égal à la taille du type **long**.<br /><br /> Objets de type **int** peuvent être déclarées comme **type signed int** ou **unsigned int**. **Type signed int** est un synonyme de **int**.|
||**__int8**, **__int16**, **__int32**, **__int64**|Entier dimensionné `__int n`, où `n` est la taille, en bits, de la variable entière. **__int8**, **__int16**, **__int32** et **__int64** sont des mots clés spécifiques à Microsoft. Tous les types ne sont disponibles sur toutes les architectures. (**__int128** n’est pas pris en charge.)|
||**long**|Type **long** (ou **long int**) est un type intégral supérieur ou égal à la taille du type **int**.<br /><br /> Objets de type **long** peuvent être déclarées comme **long signé** ou **unsigned long**. **Long signé** est un synonyme de **long**.|
||**long long**|Supérieur à un unsigned **long**.<br /><br /> Objets de type **longue** peuvent être déclarées comme **long long signé** ou **unsigned long long**. **long long signé** est un synonyme de **longue**.|
||**wchar_t**, **__wchar_t**|Une variable de type **wchar_t** désigne un type de caractères larges ou caractères multioctets. Par défaut, **wchar_t** est un type natif, mais vous pouvez utiliser [/Zc :wchar_t-)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) se **wchar_t** un typedef pour **unsigned short**. Le **__wchar_t** type est un synonyme spécifique à Microsoft pour natif **wchar_t** type.<br /><br /> Utilisez le préfixe L avant un caractère ou un littéral de chaîne pour désigner le type caractère large.|
|Virgule flottante|**float**|Type **float** est flottante plus petit type de point.|
||**double**|Type **double** est un type à virgule flottante supérieur ou un égal au type **float**, mais inférieur ou égal à la taille du type **long double**.<br /><br /> Spécifique à Microsoft : La représentation sous forme de **long double** et **double** est identique. Toutefois, **long double** et **double** sont des types distincts.|
||**long double**|Type **long double** est un flottante type virgule est supérieur ou égal au type **double**.|

**Section spécifique à Microsoft**

Le tableau suivant répertorie la quantité de stockage requise pour les types fondamentaux dans Microsoft C++.

### <a name="sizes-of-fundamental-types"></a>Tailles des types fondamentaux

|Type|Size|
|----------|----------|
|**bool**, **char**, **unsigned char**, **signed char**, **__int8**|1 octet|
|**__int16**, **court**, **unsigned short**, **wchar_t**, **__wchar_t**|2 octets|
|**float**, **__int32**, **int**, **unsigned int**, **long**, **unsigned long**|4 octets|
|**double**, **__int64**, **long double**, **long long**|8 octets|

**FIN de la section spécifique à Microsoft**

Consultez les informations relatives aux [plages de types de données](../cpp/data-type-ranges.md) pour obtenir un résumé de la plage de valeurs de chaque type.

Pour plus d'informations sur la conversion de type, consultez [Conversions standard](../cpp/standard-conversions.md).

## <a name="see-also"></a>Voir aussi

[Plages de types de données](../cpp/data-type-ranges.md)