---
description: 'En savoir plus sur : types intégrés (C++)'
title: Types intégrés (C++)
ms.date: 07/22/2020
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
ms.openlocfilehash: 601bd0742002506272ec3da7af448a4bdba96065
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268741"
---
# <a name="built-in-types-c"></a>Types intégrés (C++)

Les types intégrés (également appelés *types fondamentaux*) sont spécifiés par la norme du langage C++ et sont intégrés au compilateur. Les types intégrés ne sont définis dans aucun fichier d’en-tête. Les types intégrés sont divisés en trois catégories principales : *intégral*, *virgule flottante* et *void*. Les types intégraux représentent des nombres entiers. Les types à virgule flottante peuvent spécifier des valeurs qui peuvent avoir des parties fractionnaires. La plupart des types intégrés sont traités comme des types distincts par le compilateur. Toutefois, certains types sont des *synonymes*, ou traités comme des types équivalents par le compilateur.

## <a name="void-type"></a>Type void

Le [`void`](void-cpp.md) type décrit un ensemble de valeurs vide. Aucune variable de type ne **`void`** peut être spécifiée. Le **`void`** type est principalement utilisé pour déclarer des fonctions qui ne retournent aucune valeur ou pour déclarer des pointeurs génériques vers des données non typées ou arbitrairement typées. Toute expression peut être convertie explicitement ou castée en type **`void`** . Toutefois, ces expressions sont limitées aux utilisations suivantes :

- Instruction d'expression. (Pour plus d’informations, consultez [expressions](expressions-cpp.md).)

- Opérande gauche de l'opérateur virgule. (Pour plus d’informations, consultez la section [opérateur virgule](comma-operator.md).)

- Deuxième ou troisième opérande de l’opérateur conditionnel (`? :`). (Pour plus d’informations, consultez [expressions avec l’opérateur conditionnel](conditional-operator-q.md).)

## <a name="stdnullptr_t"></a>std :: nullptr_t

Le mot clé **`nullptr`** est une constante de pointeur null de type `std::nullptr_t` , qui peut être convertie en un type pointeur brut. Pour plus d’informations, consultez [`nullptr`](nullptr.md).

## <a name="boolean-type"></a>Type booléen

Le [`bool`](bool-cpp.md) type peut avoir des valeurs [`true`](../cpp/true-cpp.md) et [`false`](../cpp/false-cpp.md) . La taille du **`bool`** type est spécifique à l’implémentation. Consultez [tailles des types intégrés](#sizes-of-built-in-types) pour plus d’informations sur l’implémentation spécifique à Microsoft.

## <a name="character-types"></a>Types de caractères

Le **`char`** type est un type de représentation de caractères qui encode efficacement les membres du jeu de caractères d’exécution de base. Le compilateur C++ traite les variables de type **`char`** , **`signed char`** et **`unsigned char`** comme ayant des types différents.

**Spécifique à Microsoft**: les variables de type **`char`** sont promues **`int`** comme s’il s’agissait d’un type **`signed char`** par défaut, sauf si l' [`/J`](../build/reference/j-default-char-type-is-unsigned.md) option de compilation est utilisée. Dans ce cas, elles sont traitées en tant que type **`unsigned char`** et sont promues en **`int`** sans extension de signature.

Une variable de type **`wchar_t`** est un type de caractère à caractères larges ou multioctets. Utilisez le **`L`** préfixe avant un caractère ou un littéral de chaîne pour spécifier le type à caractères larges.

**Spécifique à Microsoft**: par défaut, **`wchar_t`** est un type natif, mais vous pouvez utiliser [`/Zc:wchar_t-`](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour créer **`wchar_t`** un typedef pour **`unsigned short`** . Le **`__wchar_t`** type est un synonyme spécifique à Microsoft pour le **`wchar_t`** type natif.

Le **`char8_t`** type est utilisé pour la représentation de caractères UTF-8. Elle a la même représentation que **`unsigned char`** , mais elle est traitée comme un type distinct par le compilateur. Le **`char8_t`** type est nouveau dans c++ 20. **Spécifique à Microsoft**: l’utilisation de **`char8_t`**  requiert l' [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) option de compilateur.

Le **`char16_t`** type est utilisé pour la représentation de caractères UTF-16. Elle doit être suffisamment grande pour représenter une unité de code UTF-16. Il est traité comme un type distinct par le compilateur.

Le **`char32_t`** type est utilisé pour la représentation de caractères UTF-32. Elle doit être suffisamment grande pour représenter une unité de code UTF-32. Il est traité comme un type distinct par le compilateur.

## <a name="floating-point-types"></a>Types virgule flottante

Les types à virgule flottante utilisent une représentation IEEE-754 pour fournir une approximation des valeurs fractionnaires sur un large éventail de amplitudes. Le tableau suivant répertorie les types à virgule flottante en C++ et les restrictions comparatives sur les tailles de type à virgule flottante. Ces restrictions sont imposées par la norme C++ et sont indépendantes de l’implémentation Microsoft. La taille absolue des types à virgule flottante intégrés n’est pas spécifiée dans la norme.

| Type | Contenu |
|--|--|
| **`float`** | **`float`** Le type est le plus petit type à virgule flottante en C++. |
| **`double`** | **`double`** Le type est un type à virgule flottante supérieur ou égal au type **`float`** , mais inférieur ou égal à la taille du type **`long double`** . |
| **`long double`** | **`long double`** Le type est un type à virgule flottante supérieur ou égal au type **`double`** . |

**Spécifique à Microsoft**: la représentation de **`long double`** et **`double`** est identique. Toutefois, **`long double`** et **`double`** sont traités comme des types distincts par le compilateur. Le compilateur Microsoft C++ utilise les représentations à virgule flottante IEEE-754 de 4 et 8 octets. Pour plus d’informations, consultez [représentation à virgule flottante IEEE](../build/ieee-floating-point-representation.md).

## <a name="integer-types"></a>Types d'entier

Le **`int`** type est le type entier de base par défaut. Il peut représenter tous les nombres entiers sur une plage spécifique à l’implémentation.

Une représentation d’entier *signé* est un qui peut contenir à la fois des valeurs positives et négatives. Elle est utilisée par défaut, ou lorsque le **`signed`** mot clé de modificateur est présent. Le **`unsigned`** mot clé de modificateur spécifie une représentation non *signée* qui ne peut contenir que des valeurs non négatives.

Un modificateur de taille spécifie la largeur en bits de la représentation entière utilisée. Le langage prend en charge les **`short`** **`long`** **`long long`** modificateurs, et. Un **`short`** type doit avoir une largeur d’au moins 16 bits. Un **`long`** type doit avoir une largeur de 32 bits au minimum. Un **`long long`** type doit avoir une largeur de 64 bits au minimum. La norme spécifie une relation de taille entre les types intégraux :

`1 == sizeof(char) <= sizeof(short) <= sizeof(int) <= sizeof(long) <= sizeof(long long)`

Une implémentation doit gérer à la fois les exigences de taille minimale et la relation de taille pour chaque type. Toutefois, les tailles réelles peuvent varier entre les implémentations. Consultez [tailles des types intégrés](#sizes-of-built-in-types) pour plus d’informations sur l’implémentation spécifique à Microsoft.

Le **`int`** mot clé peut être omis lorsque **`signed`** les **`unsigned`** modificateurs de taille, ou sont spécifiés. Les modificateurs et le **`int`** type, s’ils sont présents, peuvent apparaître dans n’importe quel ordre. Par exemple, **`short unsigned`** et **`unsigned int short`** font référence au même type.

### <a name="integer-type-synonyms"></a>Synonymes de type entier

Les groupes de types suivants sont considérés comme des synonymes par le compilateur :

- **`short`**, **`short int`**, **`signed short`**, **`signed short int`**

- **`unsigned short`**, **`unsigned short int`**

- **`int`**, **`signed`**, **`signed int`**

- **`unsigned`**, **`unsigned int`**

- **`long`**, **`long int`**, **`signed long`**, **`signed long int`**

- **`unsigned long`**, **`unsigned long int`**

- **`long long`**, **`long long int`**, **`signed long long`**, **`signed long long int`**

- **`unsigned long long`**, **`unsigned long long int`**

Les types d’entiers **spécifiques à Microsoft** incluent les types,, et de largeur spécifique **`__int8`** **`__int16`** **`__int32`** **`__int64`** . Ces types peuvent utiliser les **`signed`** **`unsigned`** modificateurs et. Le **`__int8`** type de données est synonyme de type, **`char`** **`__int16`** est synonyme de type **`short`** , **`__int32`** est synonyme de type **`int`** et **`__int64`** est synonyme de type **`long long`** .

## <a name="sizes-of-built-in-types"></a>Tailles des types intégrés

La plupart des types intégrés ont des tailles définies par l’implémentation. Le tableau suivant répertorie la quantité de stockage requise pour les types intégrés dans Microsoft C++. En particulier, **`long`** est de 4 octets, même sur des systèmes d’exploitation 64 bits.

| Type | Taille |
|--|--|
| **`bool`**, **`char`**, **`char8_t`**, **`unsigned char`**, **`signed char`**, **`__int8`** | 1 octet |
| **`char16_t`**, **`__int16`**, **`short`**, **`unsigned short`**, **`wchar_t`**, **`__wchar_t`** | 2 octets |
| **`char32_t`**, **`float`**, **`__int32`**, **`int`**, **`unsigned int`**, **`long`**, **`unsigned long`** | 4 octets |
| **`double`**, **`__int64`**, **`long double`**, **`long long`**, **`unsigned long long`** | 8 octets |

Consultez [plages de types de données](data-type-ranges.md) pour obtenir un résumé de la plage de valeurs de chaque type.

Pour plus d’informations sur la conversion de type, consultez [conversions standard](standard-conversions.md).

## <a name="see-also"></a>Voir aussi

[Plages de types de données](data-type-ranges.md)
