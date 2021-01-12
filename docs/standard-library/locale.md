---
description: 'En savoir plus sur : &lt; paramètres régionaux&gt;'
title: '&lt;locale&gt;'
ms.date: 11/04/2016
f1_keywords:
- <locale>
helpviewer_keywords:
- locale header
ms.assetid: ca56f9d2-7128-44da-8df1-f4c78c17fbf2
ms.openlocfilehash: 5e699bfd580c4676ae51aeea246e318c37a82d98
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126368"
---
# <a name="ltlocalegt"></a>&lt;locale&gt;

Définit des fonctions et des modèles de classe que les programmes C++ peuvent utiliser pour encapsuler et manipuler différentes conventions culturelles relatives à la représentation et à la mise en forme de données numériques, monétaires et calendrier, y compris la prise en charge de l’internationalisation pour la classification des caractères et le classement des chaînes.

## <a name="syntax"></a>Syntaxe

```cpp
#include <locale>
```

### <a name="functions"></a>Fonctions

|Fonction|Description|
|-|-|
|[has_facet](../standard-library/locale-functions.md#has_facet)|Teste si une facette particulière est stockée dans des paramètres régionaux spécifiés.|
|[isalnum](../standard-library/locale-functions.md#isalnum)|Teste si un élément figurant dans des paramètres régionaux est un caractère alphabétique ou numérique.|
|[isalpha](../standard-library/locale-functions.md#isalpha)|Teste si un élément figurant dans des paramètres régionaux est un caractère alphabétique.|
|[iscntrl](../standard-library/locale-functions.md#iscntrl)|Teste si un élément figurant dans des paramètres régionaux est un caractère de contrôle.|
|[isdigit](../standard-library/locale-functions.md#isdigit)|Teste si un élément figurant dans des paramètres régionaux est un caractère numérique.|
|[isgraph](../standard-library/locale-functions.md#isgraph)|Teste si un élément figurant dans des paramètres régionaux est un caractère alphanumérique ou de ponctuation.|
|[islower](../standard-library/locale-functions.md#islower)|Teste si un élément figurant dans des paramètres régionaux est en minuscules.|
|[isprint](../standard-library/locale-functions.md#isprint)|Teste si un élément figurant dans des paramètres régionaux est un caractère imprimable.|
|[ispunct](../standard-library/locale-functions.md#ispunct)|Teste si un élément figurant dans des paramètres régionaux est un caractère de ponctuation.|
|[isspace](../standard-library/locale-functions.md#isspace)|Teste si un élément figurant dans des paramètres régionaux est un espace blanc.|
|[isupper](../standard-library/locale-functions.md#isupper)|Teste si un élément figurant dans des paramètres régionaux est en majuscules.|
|[isxdigit](../standard-library/locale-functions.md#isxdigit)|Teste si un élément figurant dans des paramètres régionaux est un caractère utilisé pour représenter un nombre hexadécimal.|
|[ToLower](../standard-library/locale-functions.md#tolower)|Convertit un caractère en minuscule.|
|[ToUpper](../standard-library/locale-functions.md#toupper)|Convertit un caractère en majuscule.|
|[use_facet](../standard-library/locale-functions.md#use_facet)|Retourne une référence à une facette d'un type spécifié stocké dans des paramètres régionaux.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[codecvt](../standard-library/codecvt-class.md)|Modèle de classe qui fournit une facette utilisée pour la conversion entre les encodages de caractères internes et externes.|
|[codecvt_base](../standard-library/codecvt-base-class.md)|Classe de base pour la classe codecvt utilisée pour définir un type énumération appelé `result` , utilisé comme type de retour pour les fonctions membres de facette pour indiquer le résultat d’une conversion.|
|[codecvt_byname](../standard-library/codecvt-byname-class.md)|Modèle de classe dérivée qui décrit un objet pouvant servir de facette d’assemblage de paramètres régionaux donnés, permettant ainsi la récupération d’informations spécifiques à une zone culturelle concernant les conversions.|
|[COLLATE](../standard-library/collate-class.md)|Modèle de classe COLLATE qui fournit une facette qui gère les conventions de tri des chaînes.|
|[collate_byname](../standard-library/collate-byname-class.md)|Modèle de classe dérivée qui décrit un objet pouvant servir de facette d’assemblage de paramètres régionaux donnés, permettant ainsi la récupération d’informations spécifiques à une zone culturelle concernant les conventions de tri de chaînes.|
|[ctype](../standard-library/ctype-class.md)|Modèle de classe qui fournit une facette utilisée pour classifier des caractères, convertir des caractères majuscules et minuscules et entre le jeu de caractères natif et le jeu utilisé par les paramètres régionaux.|
|[CType\<char>](../standard-library/ctype-char-class.md)|Classe qui est une spécialisation explicite de la classe template `ctype<CharType>` à taper **`char`** , décrivant un objet pouvant servir de facette de paramètres régionaux pour caractériser diverses propriétés d’un caractère de type **`char`** .|
|[ctype_base](../standard-library/ctype-base-class.md)|Classe de base de la classe ctype utilisée pour définir des types énumération utilisés pour classifier ou tester les caractères, individuellement ou dans des plages entières.|
|[ctype_byname](../standard-library/ctype-byname-class.md)|Modèle de classe dérivée qui décrit un objet pouvant servir de facette CType de paramètres régionaux donnés, permettant ainsi la classification des caractères et la conversion des caractères entre les jeux de caractères et les jeux de caractères spécifiés.|
|[locale](../standard-library/locale-class.md)|Classe qui décrit un objet de paramètres régionaux encapsulant des informations spécifiques à la culture sous la forme d'un ensemble de facettes qui définissent collectivement un environnement localisé spécifique.|
|[messages](../standard-library/messages-class.md)|Modèle de classe qui décrit un objet pouvant servir de facette de paramètres régionaux pour récupérer des messages localisés à partir d’un catalogue de messages internationalisés pour des paramètres régionaux donnés.|
|[messages_base](../standard-library/messages-base-class.md)|Classe de base qui décrit un **`int`** type pour le catalogue de messages.|
|[messages_byname](../standard-library/messages-byname-class.md)|Modèle de classe dérivée qui décrit un objet pouvant servir de facette de message de paramètres régionaux donnés, permettant ainsi la récupération de messages localisés.|
|[money_base](../standard-library/money-base-class.md)|Classe de base de la classe ctype utilisée pour définir des types énumération utilisés pour classifier ou tester les caractères, individuellement ou dans des plages entières.|
|[money_get](../standard-library/money-get-class.md)|Modèle de classe qui décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de séquences de type **CharType** en valeurs monétaires.|
|[money_put](../standard-library/money-put-class.md)|Modèle de classe qui décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de valeurs monétaires en séquences de type **CharType**.|
|[moneypunct](../standard-library/moneypunct-class.md)|Modèle de classe qui décrit un objet pouvant servir de facette de paramètres régionaux pour décrire les séquences de type **CharType** utilisées pour représenter un champ d’entrée monétaire ou un champ de sortie monétaire.|
|[moneypunct_byname](../standard-library/moneypunct-byname-class.md)|Modèle de classe dérivée qui décrit un objet pouvant servir de facette moneypunct de paramètres régionaux donnés, permettant ainsi la mise en forme des champs d’entrée ou de sortie monétaires.|
|[num_get](../standard-library/num-get-class.md)|Modèle de classe qui décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de séquences de type **CharType** en valeurs numériques.|
|[num_put](../standard-library/num-put-class.md)|Modèle de classe qui décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de valeurs numériques en séquences de type **CharType**.|
|[numpunct](../standard-library/numpunct-class.md)|Modèle de classe qui décrit un objet pouvant servir de facette locale pour décrire les séquences de type **CharType** utilisées pour représenter des informations sur la mise en forme et la ponctuation d’expressions numériques et booléennes.|
|[numpunct_byname](../standard-library/numpunct-byname-class.md)|Modèle de classe dérivée qui décrit un objet pouvant servir de facette moneypunct de paramètres régionaux donnés, permettant ainsi la mise en forme et la ponctuation d’expressions numériques et booléennes.|
|[time_base](../standard-library/time-base-class.md)|Classe qui sert de classe de base pour les facettes de la time_get de modèle de classe, définissant uniquement le type énuméré DateOrder et plusieurs constantes de ce type.|
|[time_get](../standard-library/time-get-class.md)|Modèle de classe qui décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de séquences de type **CharType** en valeurs d’heure.|
|[time_get_byname](../standard-library/time-get-byname-class.md)|Modèle de classe dérivée qui décrit un objet pouvant servir de facette de paramètres régionaux de type time_get \<**CharType**, **InputIterator**> .|
|[time_put](../standard-library/time-put-class.md)|Modèle de classe qui décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de valeurs d’heure en séquences de type **CharType**.|
|[time_put_byname](../standard-library/time-put-byname-class.md)|Modèle de classe dérivée qui décrit un objet pouvant servir de facette de paramètres régionaux de type `time_put` \<**CharType**, **OutputIterator**> .|
|[Classe wbuffer_convert](../standard-library/wbuffer-convert-class.md)|Décrit une mémoire tampon de flux qui contrôle la transmission des éléments vers et à partir d'une mémoire tampon de flux d'octets.|
|[Classe wstring_convert](../standard-library/wstring-convert-class.md)|Modèle de classe qui effectue des conversions entre une chaîne étendue et une chaîne d’octets.|

## <a name="see-also"></a>Voir aussi

[Pages de codes](../c-runtime-library/code-pages.md)\
[Chaînes de noms de paramètres régionaux, de langues et de pays/région](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
