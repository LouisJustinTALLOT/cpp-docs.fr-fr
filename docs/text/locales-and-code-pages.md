---
description: 'En savoir plus sur : paramètres régionaux et pages de codes'
title: Paramètres régionaux et pages de codes
ms.date: 11/04/2016
helpviewer_keywords:
- locales [C++], about locales
- locale IDs [C++]
- locales [C++]
- code pages [C++]
- code pages [C++], dynamically changing
- character sets [C++], code pages
- multibyte code pages [C++]
- character sets [C++], locales
- localization [C++], code pages
- localization [C++], locales
- code pages [C++], locales
- conventions [C++], international character support
ms.assetid: bd937361-b6d3-4c98-af95-beb7c903187b
ms.openlocfilehash: f8b5310d7712617b1397bc42ef6ec58e5b3297ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207200"
---
# <a name="locales-and-code-pages"></a>Paramètres régionaux et pages de codes

Un ID de paramètres régionaux reflète les conventions locales et la langue d’une région géographique particulière. Une langue donnée peut être parlée dans plus d’un pays/région ; par exemple, le portugais est parlé au Brésil et au Portugal. À l’inverse, un pays ou une région peut avoir plusieurs langues officielles. Par exemple, le Canada a deux langues : l’anglais et le français. Par conséquent, le Canada a deux paramètres régionaux distincts : Canadian-English et canadien-français. Certaines catégories dépendent des paramètres régionaux, notamment la mise en forme des dates et le format d'affichage des valeurs monétaires.

La langue détermine les conventions de mise en forme du texte et des données, tandis que le pays ou la région détermine les conventions locales. Chaque langue a un mappage unique, représenté par des pages de codes, qui inclut des caractères autres que ceux de l’alphabet (tels que des signes de ponctuation et des chiffres). Une page de codes est un jeu de caractères qui est lié à la langue. Par conséquent, les [paramètres régionaux](../c-runtime-library/locale.md) sont une combinaison unique de langue, pays/région et page de codes. Les paramètres régionaux et la page de codes peuvent être modifiés au moment de l’exécution en appelant la fonction [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) .

Différentes langues peuvent utiliser des pages de codes différentes. Par exemple, la page de codes ANSI 1252 est utilisée pour l’anglais et la plupart des langues européennes, et la page de codes ANSI 932 est utilisée pour le Kanji japonais. Presque toutes les pages de codes partagent le jeu de caractères ASCII pour les 128 caractères les plus faibles (0x00 à 0x7F).

Toute page de codes sur un octet peut être représentée dans une table (avec 256 entrées) comme mappage de valeurs d’octets à des caractères (y compris des chiffres et des signes de ponctuation) ou des glyphes. Toutes les pages de codes multioctets peuvent également être représentées sous la forme d’une table très volumineuse (avec des entrées de 64 Ko) de valeurs codées sur deux octets à des caractères. Toutefois, dans la pratique, il est généralement représenté sous la forme d’un tableau pour les premiers caractères 256 (codés sur un octet) et comme plages pour les valeurs codées sur deux octets.

Pour plus d’informations sur les pages de codes, consultez [Pages de codes](../c-runtime-library/code-pages.md).

La bibliothèque Runtime C possède deux types de pages de codes internes : paramètres régionaux et multioctets. Vous pouvez modifier la page de codes en cours lors de l’exécution du programme (consultez la documentation des fonctions [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) et [_setmbcp](../c-runtime-library/reference/setmbcp.md) ). En outre, la bibliothèque Runtime peut obtenir et utiliser la valeur de la page de codes du système d’exploitation, qui est constante pour la durée de l’exécution du programme.

Lorsque la page de codes des paramètres régionaux change, le comportement de l’ensemble de fonctions dépendant des paramètres régionaux passe à celui dicté par la page de codes choisie. Par défaut, toutes les fonctions dépendantes des paramètres régionaux commencent à s’exécuter avec une page de codes de paramètres régionaux propre aux paramètres régionaux « C ». Vous pouvez modifier la page de codes des paramètres régionaux internes (ainsi que d’autres propriétés spécifiques aux paramètres régionaux) en appelant la `setlocale` fonction. Un appel à `setlocale` (LC_ALL, "") définit les paramètres régionaux à ceux indiqués par les paramètres régionaux utilisateur du système d’exploitation.

De même, lorsque la page de codes multioctets change, le comportement des fonctions multioctets passe à celui imposé par la page de codes choisie. Par défaut, toutes les fonctions multioctets commencent à s’exécuter avec une page de codes multioctets correspondant à la page de codes par défaut du système d’exploitation. Vous pouvez modifier la page de codes multioctets interne en appelant la `_setmbcp` fonction.

La fonction Runtime C `setlocale` définit, modifie ou interroge tout ou partie des informations relatives aux paramètres régionaux du programme actif. La routine [_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) est une version à caractères larges de `setlocale` ; les arguments et les valeurs de retour de `_wsetlocale` sont des chaînes à caractères larges.

## <a name="see-also"></a>Voir aussi

[Unicode et MBCS](../text/unicode-and-mbcs.md)<br/>
[Avantages de la portabilité des jeux de caractères](../text/benefits-of-character-set-portability.md)
