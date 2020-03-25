---
title: Types intégrés (C++)
ms.date: 12/11/2019
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
- char8_t_cpp
- char16_t_cpp
- char32_t_cpp
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
- long keyword [C++]
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
ms.openlocfilehash: 14d96453785a55f625b5467458f9cf79e6739acf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188605"
---
# <a name="built-in-types-c"></a>Types intégrés (C++)

Les types intégrés (également appelés *types fondamentaux*) sont spécifiés par la C++ norme du langage et sont intégrés au compilateur. Les types intégrés ne sont pas définis dans un fichier d’en-tête. Les types intégrés sont divisés en trois catégories : intégral, virgule flottante et void. Les types intégraux sont capables de gérer les nombres entiers. Les types virgule flottante peuvent spécifier des valeurs pouvant avoir des parties fractionnaires.

Le type [void](void-cpp.md) décrit un ensemble de valeurs vide. Aucune variable de type **void** ne peut être spécifiée ; elle est principalement utilisée pour déclarer des fonctions qui ne retournent aucune valeur ou pour déclarer des pointeurs génériques vers des données non typées ou arbitraires. Toute expression peut être convertie explicitement ou castée en type **void**. Toutefois, ces expressions sont limitées aux utilisations suivantes :

- Instruction d'expression. (Pour plus d’informations, consultez [expressions](expressions-cpp.md).)

- Opérande gauche de l'opérateur virgule. (Pour plus d’informations, consultez la section [opérateur virgule](comma-operator.md).)

- Deuxième ou troisième opérande de l’opérateur conditionnel (`? :`). (Pour plus d’informations, consultez [expressions avec l’opérateur conditionnel](conditional-operator-q.md).)

Le tableau suivant décrit les restrictions sur les tailles de type par rapport aux autres. Ces restrictions sont imposées par C++ la norme et sont indépendantes de l’implémentation Microsoft. La taille absolue de certains types intégrés n’est pas spécifiée dans la norme.

### <a name="built-in-type-size-restrictions"></a>Restrictions de taille de type intégré

|Category|Type|Contents|
|--------------|----------|--------------|
|Intégral|**char**|Le type **char** est un type intégral qui contient généralement les membres du jeu de caractères d’exécution de base ; par défaut, il C++s’agit de ASCII dans Microsoft.<br /><br /> Le C++ compilateur traite les variables de type **char**, **signed char**et **unsigned char** comme ayant des types différents. Les variables de type **char** sont promues en **int** comme s’il s’agissait de type **signed char** par défaut, sauf si l’option de compilation/j est utilisée. Dans ce cas, elles sont traitées en tant que type **unsigned char** et sont promues en **int** sans extension de signature.|
||**bool**|Le type **bool** est un type intégral qui peut avoir l’une des deux valeurs **true** ou **false**. Sa taille n'est pas spécifiée.|
||**short**|Le type **short int** (ou simplement **short**) est un type intégral supérieur ou égal à la taille du type **char**, et inférieur ou égal à la taille du type **int**.<br /><br /> Les objets de type **short** peuvent être déclarés comme étant **signed** short ou **unsigned short**. **Signed Short** est un synonyme de **short**.|
||**int**|Le type **int** est un type intégral supérieur ou égal à la taille de type **short int**, et inférieur ou égal à la taille du type **long**.<br /><br /> Les objets de type **int** peuvent être déclarés comme **signed int** ou **unsigned int**. **Signed int** est un synonyme de **int**.|
||**__int8**, **__int16**, **__int32**, **__int64**|Entier dimensionné `__int n`, où `n` est la taille, en bits, de la variable entière. **__int8**, **__int16**, **__int32** et **__Int64** sont des mots clés spécifiques à Microsoft. Tous les types ne sont pas disponibles sur toutes les architectures. ( **__int128** n’est pas pris en charge.)|
||**long**|Le type **long** (ou **long int**) est un type intégral supérieur ou égal à la taille de type **int**. (Sur Windows, la taille de la **valeur** est identique à celle de **int**.)<br /><br /> Les objets de type **long** peuvent être déclarés comme étant **signed** long ou **unsigned long**. **Long signé** est un synonyme de **long**.|
||**long long**|Plus grand qu’un **long**non signé.<br /><br /> Les objets de type **long** long peuvent être déclarés comme étant **signed long** long ou **unsigned long**long. **long long long est un** synonyme de **long**long.|
||**wchar_t**, **__wchar_t**|Une variable de type **wchar_t** désigne un type de caractère à caractères larges ou multioctets. Par défaut, **wchar_t** est un type natif, mais vous pouvez utiliser [/Zc : wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour créer **wchar_t** un typedef pour **unsigned short**. Le type de **__wchar_t** est un synonyme spécifique à Microsoft pour le type de **wchar_t** natif.<br /><br /> Utilisez le préfixe L avant un caractère ou un littéral de chaîne pour désigner le type caractère large.|
|Virgule flottante|**float**|Le type **float** est le plus petit type à virgule flottante.|
||**double**|Le type **double** est un type à virgule flottante supérieur ou égal au type **float**, mais inférieur ou égal à la taille du type **long double**.<br /><br /> Spécifique à Microsoft : la représentation de **long double** et **double** est identique. Toutefois, les types **long double** et **double** sont des types distincts.|
||**long double**|Le type **long double** est un type à virgule flottante supérieur ou égal au type **double**.|

**Section spécifique de Microsoft**

Le tableau suivant répertorie la quantité de stockage requise pour les types intégrés dans Microsoft C++. En particulier, Notez que **long** est de 4 octets, même sur les systèmes d’exploitation 64 bits.

### <a name="sizes-of-built-in-types"></a>Tailles des types intégrés

|Type|Size|
|----------|----------|
|**bool**, **char**, **unsigned char**, signed **char**, **__int8**|1 octet|
|**__int16**, **short**, **unsigned short**, **wchar_t** **__wchar_t**|2 octets|
|**float**, **__int32**, **int**, **unsigned int**, **long**, **unsigned long**|4 octets|
|**double**, **__int64**, **long double**, long **long**|8 octets|

**Fin de la section spécifique de Microsoft**

Consultez les informations relatives aux [plages de types de données](data-type-ranges.md) pour obtenir un résumé de la plage de valeurs de chaque type.

Pour plus d'informations sur la conversion de type, consultez [Conversions standard](standard-conversions.md).

## <a name="see-also"></a>Voir aussi

[plages de types de données](data-type-ranges.md)
