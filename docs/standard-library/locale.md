---
title: '&lt;locale&gt;'
ms.date: 11/04/2016
f1_keywords:
- <locale>
- locale/std::<locale>
- std::<locale>
helpviewer_keywords:
- locale header
ms.assetid: ca56f9d2-7128-44da-8df1-f4c78c17fbf2
ms.openlocfilehash: 54d6f5306f4517c6450f36051df51385d8d8f578
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494302"
---
# <a name="ltlocalegt"></a>&lt;locale&gt;

Définit les classes de modèle et les fonctions que les programmes C++ peuvent utiliser pour encapsuler et manipuler différentes conventions culturelles concernant la représentation et la mise en forme des données numériques, monétaires et de calendrier, y compris la prise en charge de l'internationalisation de la classification des caractères et du classement des chaînes.

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
|[tolower](../standard-library/locale-functions.md#tolower)|Convertit un caractère en minuscule.|
|[toupper](../standard-library/locale-functions.md#toupper)|Convertit un caractère en majuscule.|
|[use_facet](../standard-library/locale-functions.md#use_facet)|Retourne une référence à une facette d'un type spécifié stocké dans des paramètres régionaux.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[codecvt](../standard-library/codecvt-class.md)|Classe de modèle qui fournit une facette utilisée pour convertir des données entre les encodages de caractères interne et externe.|
|[codecvt_base](../standard-library/codecvt-base-class.md)|Une classe de base pour la classe codecvt qui sert à définir un type d’énumération appelé `result`, utilisé comme type de retour pour les fonctions membres de facette pour indiquer le résultat d’une conversion.|
|[codecvt_byname](../standard-library/codecvt-byname-class.md)|Classe de modèle dérivée qui décrit un objet susceptible de servir de facette d'assemblage de paramètres régionaux donnés, permettant ainsi la récupération d'informations spécifiques à une zone culturelle concernant les conversions.|
|[collate](../standard-library/collate-class.md)|Classe de modèle d'assemblage fournissant une facette qui gère les conventions de tri de chaîne.|
|[collate_byname](../standard-library/collate-byname-class.md)|Classe de modèle dérivée qui décrit un objet susceptible de servir de facette d'assemblage de paramètres régionaux donnés, permettant ainsi la récupération d'informations spécifiques à une zone culturelle concernant les conventions de tri de chaîne.|
|[ctype](../standard-library/ctype-class.md)|Classe de modèle fournissant une facette utilisée pour la classification des caractères et la conversion entre majuscules et minuscules et entre le jeu de caractères natif et celui utilisé par les paramètres régionaux.|
|[ctype\<char>](../standard-library/ctype-char-class.md)|Une classe qui est une spécialisation explicite de la classe de modèle `ctype<CharType>` à taper **char**, décrivant un objet pouvant servir de facette de paramètres régionaux pour caractériser diverses propriétés d’un caractère de type **char**.|
|[ctype_base](../standard-library/ctype-base-class.md)|Classe de base de la classe ctype utilisée pour définir des types énumération utilisés pour classifier ou tester les caractères, individuellement ou dans des plages entières.|
|[ctype_byname](../standard-library/ctype-byname-class.md)|Classe de modèle dérivée qui décrit un objet pouvant servir de facette ctype de paramètres régionaux donnés, permettant ainsi la classification des caractères et la conversion des caractères entre des jeux de caractères natifs, de casse ou de paramètres régionaux spécifiés.|
|[locale](../standard-library/locale-class.md)|Classe qui décrit un objet de paramètres régionaux encapsulant des informations spécifiques à la culture sous la forme d'un ensemble de facettes qui définissent collectivement un environnement localisé spécifique.|
|[messages](../standard-library/messages-class.md)|Classe de modèle qui décrit un objet pouvant servir de facette de paramètres régionaux pour récupérer des messages localisés à partir d'un catalogue de messages internationalisés pour des paramètres régionaux donnés.|
|[messages_base](../standard-library/messages-base-class.md)|Une classe de base qui décrit un **int** type pour le catalogue de messages.|
|[messages_byname](../standard-library/messages-byname-class.md)|Classe de modèle dérivée qui décrit un objet pouvant servir de facette de message de paramètres régionaux donnés, permettant ainsi la récupération de messages localisés.|
|[money_base](../standard-library/money-base-class.md)|Classe de base de la classe ctype utilisée pour définir des types énumération utilisés pour classifier ou tester les caractères, individuellement ou dans des plages entières.|
|[money_get](../standard-library/money-get-class.md)|Classe de modèle qui décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de séquences de type **CharType** en valeurs monétaires.|
|[money_put](../standard-library/money-put-class.md)|Classe de modèle qui décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de valeurs monétaires en séquences de type **CharType**.|
|[moneypunct](../standard-library/moneypunct-class.md)|Classe de modèle qui décrit un objet pouvant servir de facette de paramètres régionaux pour décrire les séquences de type **CharType** utilisé pour représenter un champ d’entrée monétaire ou un champ de sortie monétaire.|
|[moneypunct_byname](../standard-library/moneypunct-byname-class.md)|Classe de modèle dérivée qui décrit un objet pouvant servir de facette moneypunct de paramètres régionaux donnés, permettant ainsi la mise en forme de champs d'entrée ou de sortie monétaires.|
|[num_get](../standard-library/num-get-class.md)|Classe de modèle qui décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de séquences de type **CharType** en valeurs numériques.|
|[num_put](../standard-library/num-put-class.md)|Classe de modèle qui décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de valeurs numériques en séquences de type **CharType**.|
|[numpunct](../standard-library/numpunct-class.md)|Classe de modèle qui décrit un objet pouvant servir de facette locale pour décrire les séquences de type **CharType** utilisé pour représenter des informations sur la mise en forme et la ponctuation d’expressions numériques et booléennes.|
|[numpunct_byname](../standard-library/numpunct-byname-class.md)|Classe de modèle dérivée qui décrit un objet pouvant servir de facette moneypunct de paramètres régionaux donnés, permettant la mise en forme et la ponctuation d'expressions numériques et booléennes.|
|[time_base](../standard-library/time-base-class.md)|Classe qui sert de classe de base pour les facettes de la classe de modèle time_get, définissant simplement le type énuméré dateorder et plusieurs constantes de ce type.|
|[time_get](../standard-library/time-get-class.md)|Classe de modèle qui décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de séquences de type **CharType** en valeurs temporelles.|
|[time_get_byname](../standard-library/time-get-byname-class.md)|Classe de modèle dérivée qui décrit un objet pouvant servir de facette de paramètres régionaux du typetime_get\<**CharType**, **InputIterator**>.|
|[time_put](../standard-library/time-put-class.md)|Classe de modèle qui décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler les conversions de valeurs d’heure en séquences de type **CharType**.|
|[time_put_byname](../standard-library/time-put-byname-class.md)|Classe de modèle dérivée qui décrit un objet pouvant servir de facette de paramètres régionaux de type `time_put` \< **CharType**, **OutputIterator**>.|
|[wbuffer_convert, classe](../standard-library/wbuffer-convert-class.md)|Décrit une mémoire tampon de flux qui contrôle la transmission des éléments vers et à partir d'une mémoire tampon de flux d'octets.|
|[wstring_convert, classe](../standard-library/wstring-convert-class.md)|Classe de modèle qui effectue des conversions entre une chaîne étendue et une chaîne d'octets.|

## <a name="see-also"></a>Voir aussi

[Pages de codes](../c-runtime-library/code-pages.md)<br/>
[Chaînes relatives aux noms des paramètres régionaux, aux langues et au pays/à la région](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
