---
title: Jeux de caractères codés sur un octet et multioctets
description: Introduction aux jeux de caractères codés sur un et plusieurs octets dans la bibliothèque Microsoft Runtime.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- SBCS (single byte character set)
- MBCS [C++], about MBCS
- character sets [C++], multibyte
- character sets [C++], single byte
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
ms.openlocfilehash: 6668285915ab9f1939c1baf8a2d3da2d00543528
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590171"
---
# <a name="single-byte-and-multibyte-character-sets"></a>Jeux de caractères codés sur un octet et multioctets

Le jeu de caractères ASCII définit les caractères compris dans la plage 0x00 à 0x7F. Il existe plusieurs autres jeux de caractères, principalement européens, qui définissent les caractères de la plage 0x00 - 0x7F de la même façon que le jeu de caractères ASCII, et qui définissent également un jeu de caractères étendu de la plage 0x80 - 0xFF.  Un jeu de caractères codés sur un octet (SBCS) de 8 bits est suffisant pour représenter le jeu de caractères ASCII, ainsi que les jeux de caractères de nombreuses langues européennes. Toutefois, certains jeux de caractères non européens, tels que le Kanji japonais, incluent beaucoup plus de caractères que ceux qui peuvent être représentés dans un schéma de codage codé sur un octet, et nécessitent donc un encodage MBCS (multibytes-Character Set).

> [!NOTE]
> De nombreuses routines SBCS de la bibliothèque runtime Microsoft peuvent gérer les octets, les caractères et les chaînes multioctets. Plusieurs jeux de caractères multioctets définissent le jeu de caractères ASCII comme un sous-ensemble. Dans de nombreux jeux de caractères multioctets, chaque caractère de la plage 0x00-0x7F est identique au caractère qui a la même valeur dans le jeu de caractères ASCII. Par exemple, dans les chaînes de caractères ASCII et MBCS, un caractère null d’un octet ('\0') a la valeur 0x00 et représente le caractère null de fin.

Un jeu de caractères multioctets peut comporter des caractères d’un octet et de 2 octets. Une chaîne de caractères multioctets peut contenir un mélange de caractères codés sur un octet et sur deux octets. Un caractère codé sur deux octets est constitué d’un octet de tête et d’un octet de fin. Dans un jeu de caractères multioctets, les octets de tête sont compris dans une plage et les octets de fin dans une autre. Lorsque ces plages se chevauchent, vous devrez peut-être évaluer le contexte pour déterminer si un octet donné fonctionne comme un octet de tête ou un octet de fin.

## <a name="see-also"></a>Voir aussi

[Internationalisation](../c-runtime-library/internationalization.md)<br/>
[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
