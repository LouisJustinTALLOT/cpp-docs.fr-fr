---
title: Texte et chaînes en Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- programming [C++], international
- multiple language support [C++]
- Unicode [C++]
- international applications [C++], about international applications
- portability [C++]
- translation [C++], character sets
- non-European characters [C++]
- character sets [C++]
- globalization [C++]
- Japanese characters [C++]
- Kanji character support [C++]
- local character sets [C++]
- ASCII characters [C++]
- character sets [C++], about character sets
- localization [C++], character sets
- translating code [C++]
- localization [C++]
- character sets [C++], non-European
- portability [C++], character sets
- MBCS [C++], international programming
ms.assetid: a1bb27ac-abe5-4c6b-867d-f761d4b93205
ms.openlocfilehash: 80b7139996fddc82b206828d4a036922fa1446d5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167600"
---
# <a name="text-and-strings-in-visual-c"></a>Texte et chaînes en Visual C++

Un aspect important du développement d’applications pour les marchés internationaux est la représentation adéquate des jeux de caractères locaux. Le jeu de caractères ASCII définit les caractères de la plage 0x00 à 0x7F. D’autres jeux de caractères, essentiellement européens, définissent les caractères dans la plage 0x00 à 0x7F de la même façon que le jeu de caractères ASCII et définissent également un jeu de caractères étendus de 0x80 à 0xFF. Ainsi, un jeu de caractères codés sur un octet (SBCS) de 8 bits est suffisant pour représenter le jeu de caractères ASCII, ainsi que les jeux de caractères de nombreuses langues européennes. Toutefois, certains jeux de caractères non européens, tels que le Kanji japonais, incluent beaucoup plus de caractères qu’un schéma de codage codé sur un octet, et nécessitent donc un codage MBCS (Multibyte-Character Set).

## <a name="in-this-section"></a>Dans cette section

[Unicode et MBCS](../text/unicode-and-mbcs.md)<br/>
Décrit la prise C++ en charge visuelle pour la programmation Unicode et MBCS.

[Prise en charge pour Unicode](../text/support-for-unicode.md)<br/>
Décrit Unicode, une spécification pour la prise en charge de tous les jeux de caractères, y compris les jeux de caractères qui ne peuvent pas être représentés dans un seul octet.

[Prise en charge des jeux de caractères multioctets (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
Décrit MBCS, une alternative à Unicode pour la prise en charge des jeux de caractères, tels que le japonais et le chinois, qui ne peuvent pas être représentés dans un seul octet.

[Mappages de texte générique dans tchar.h](../text/generic-text-mappings-in-tchar-h.md)<br/>
Fournit des mappages de texte générique spécifiques à Microsoft pour de nombreux types de données, routines et autres objets.

[Guide pratique pour effectuer une conversion entre différents types de chaînes](../text/how-to-convert-between-various-string-types.md)<br/>
Montre comment convertir différents types de C++ chaînes visuelles en d’autres chaînes.

## <a name="related-sections"></a>Sections connexes

[Internationalisation](../c-runtime-library/internationalization.md)<br/>
Décrit la prise en charge internationale dans la bibliothèque Runtime C.

[Exemples internationaux](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/International)<br/>
Fournit des liens vers des exemples illustrant l’internationalisation dans Visual C++.

[Chaînes de langue et de pays/région](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
Fournit les chaînes de langue et de pays/région dans la bibliothèque Runtime C.
