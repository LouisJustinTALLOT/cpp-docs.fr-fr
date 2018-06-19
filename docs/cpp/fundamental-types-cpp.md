---
title: Types fondamentaux (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c24ee360f1c14aa9b355f45ec1c12877efa306c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417325"
---
# <a name="fundamental-types--c"></a>Types fondamentaux (C++)
En C++, les types fondamentaux sont divisés en trois catégories : intégral, virgule flottante et void. Les types intégraux sont capables de gérer les nombres entiers. Les types virgule flottante peuvent spécifier des valeurs pouvant avoir des parties fractionnaires.  
  
 Le type [void](../cpp/void-cpp.md) décrit un ensemble de valeurs vide. Aucune variable de type `void` ne peut être spécifiée. Ce type est surtout utilisé pour déclarer des fonctions qui ne retournent aucune valeur ou pour déclarer des pointeurs génériques vers des données non typées ou des données typées arbitrairement. Toute expression peut être convertie explicitement ou castée en type `void`. Toutefois, ces expressions sont limitées aux utilisations suivantes :  
  
-   Instruction d'expression. (Pour plus d'informations, consultez [Expressions](../cpp/expressions-cpp.md).)  
  
-   Opérande gauche de l'opérateur virgule. (Pour plus d'informations, consultez [Opérateur virgule](../cpp/comma-operator.md) .)  
  
-   Le deuxième ou troisième opérande de l’opérateur conditionnel (`? :`). (Pour plus d'informations, consultez [Expressions avec l'opérateur conditionnel](../cpp/conditional-operator-q.md) .)  
  
 Le tableau suivant décrit les restrictions relatives aux tailles des types. Ces restrictions sont indépendantes de l'implémentation Microsoft.  
  
### <a name="fundamental-types-of-the-c-language"></a>Types fondamentaux du langage C++  
  
|Category|Type|Sommaire|  
|--------------|----------|--------------|  
|Intégral|`char`|Le type `char` est un type intégral qui contient généralement les membres du jeu de caractères d’exécution de base. Par défaut, il s’agit des caractères ASCII en Microsoft C++.<br /><br /> Le compilateur C++ traite les variables de type `char`, `signed` `char`et `unsigned` `char` comme ayant différents types. Les variables de type `char` sont promues en `int` , car elles sont de type `signed` `char` par défaut, sauf si l’option de compilation /J est utilisée. Dans ce cas, elles sont traitées comme type `unsigned` `char` et sont promues en `int` sans extension de signature.|  
||`bool`|Le type `bool` est un type intégral qui peut avoir l’une des deux valeurs `true` ou `false`. Sa taille n'est pas spécifiée.|  
||`short`|Le type `short` `int` (ou simplement `short`) est un type intégral supérieur ou égal à la taille du type `char`, et inférieur ou égal à la taille du type `int`.<br /><br /> Les objets de type `short` peuvent être déclarés comme étant `signed` `short` ou `unsigned short`. `Signed short` est un synonyme de `short`.|  
||`int`|Le type `int` est un type intégral supérieur ou égal à la taille du type `short` `int`, et inférieur ou égal à la taille du type `long`.<br /><br /> Les objets de type `int` peuvent être déclarés comme étant `signed` `int` ou `unsigned` `int`. `Signed` `int` est un synonyme de `int`.|  
||`__int8`, `__int16`, `__int32`, `__int64`|Entier dimensionné `__int n`, où `n` est la taille, en bits, de la variable entière. `__int8`, `__int16`, `__int32` et `__int64` sont des mots clés spécifiques à Microsoft. Tous les types ne sont disponibles sur toutes les architectures. `(__int128` est pas pris en charge.)|  
||`long`|Le type `long` (ou `long` `int`) est un type intégral supérieur ou égal à la taille du type `int`.<br /><br /> Les objets de type `long` peuvent être déclarés comme étant `signed` `long` ou `unsigned` `long`. `Signed` `long` est un synonyme de `long`.|  
||`long` `long`|Plus grand qu’un `long`non signé.<br /><br /> Les objets de type `long long` peuvent être déclarés comme étant `signed` `long long` ou `unsigned` `long long`. `signed` `long long` est un synonyme de `long long`.|  
||`wchar_t`, `__wchar_t`|Une variable de type `wchar_t` désigne un type caractères larges ou caractères multioctets. Par défaut, `wchar_t` est un type natif, mais vous pouvez utiliser [/Zc:wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour faire de `wchar_t` un typedef pour `unsigned short`. Le type `__wchar_t` est un synonyme spécifique à Microsoft pour le type natif `wchar_t` .<br /><br /> Utilisez le préfixe L avant un caractère ou un littéral de chaîne pour désigner le type caractère large.|  
|Virgule flottante|`float`|Le type `float` est le plus petit type virgule flottante.|  
||`double`|Le type `double` est un type virgule flottante supérieur ou égal au type `float`, mais inférieur ou égal à la taille du type `long` `double`.<br /><br /> Spécifique à Microsoft : la représentation de `long double` et `double` est identique. Toutefois, `long double` et `double` sont des types distincts.|  
||`long double`|Le type `long` `double` est un type virgule flottante supérieur ou égal au type `double`.|  
  
 **Section spécifique à Microsoft**  
  
 Le tableau suivant répertorie la quantité de stockage requise pour les types fondamentaux dans Microsoft C++.  
  
### <a name="sizes-of-fundamental-types"></a>Tailles des types fondamentaux  
  
|Type|Size|  
|----------|----------|  
|`bool`, `char`, `unsigned char`, `signed char`, `__int8`|1 octet|  
|`__int16`, `short`, `unsigned short`, `wchar_t`, `__wchar_t`|2 octets|  
|`float`, `__int32`, `int`, `unsigned int`, `long`, `unsigned long`|4 octets|  
|`double`, `__int64`, `long double`, `long long`|8 octets|  
  
 **FIN de la section spécifique à Microsoft**  
  
 Consultez les informations relatives aux [plages de types de données](../cpp/data-type-ranges.md) pour obtenir un résumé de la plage de valeurs de chaque type.  
  
 Pour plus d'informations sur la conversion de type, consultez [Conversions standard](../cpp/standard-conversions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Plages de types de données](../cpp/data-type-ranges.md)