---
title: Texte et chaînes en Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8eaf5425bab79d31391e6ccd82e03c667de1271c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016624"
---
# <a name="text-and-strings-in-visual-c"></a>Texte et chaînes en Visual C++
Un aspect important du développement d’applications pour les marchés internationaux est la représentation adéquate des jeux de caractères local. Le jeu de caractères ASCII définit les caractères dans la plage 0 x 00 à 0x7F. Voici les autres jeux de caractères, principalement européens, qui définissent les caractères dans la plage 0 x 00 à 0x7F de façon identique au jeu de caractères ASCII et également définir un étendue jeu de caractères à partir de 0 x 80 à 0xFF. Par conséquent, un ensemble de 8 bits, en caractères sur un octet (SBCS) est suffisant pour représenter le jeu de caractères ASCII, ainsi que les jeux de caractères de nombreuses langues européennes. Toutefois, certains jeux de caractères non européens, tels que les Kanji japonais, comprennent plus de caractères qu’un schéma de codage d’un octet peut représenter et nécessitent donc le jeu de caractères multioctets (MBCS) encodage.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Unicode et MBCS](../text/unicode-and-mbcs.md)  
 Décrit la prise en charge de Visual C++ pour la programmation Unicode et MBCS.  
  
 [Prise en charge pour Unicode](../text/support-for-unicode.md)  
 Décrit l’Unicode, une spécification pour prendre en charge tous les jeux de caractères, y compris les jeux de caractères qui ne peuvent pas être représentés dans un seul octet.  
  
 [Prise en charge des jeux de caractères multioctets (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)  
 Explique MBCS, une alternative au format Unicode pour prendre en charge les jeux de caractères japonais et chinois, qui ne peut pas être représentée dans un seul octet.  
  
 [Mappages de texte générique dans Tchar.h](../text/generic-text-mappings-in-tchar-h.md)  
 Fournit des mappages de texte générique spécifiques à Microsoft pour nombreux types de données, routines et autres objets.  
  
 [Guide pratique pour effectuer une conversion entre différents types de chaînes](../text/how-to-convert-between-various-string-types.md)  
 Montre comment convertir différents types de chaînes Visual C++ en d’autres chaînes.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Internationalisation](../c-runtime-library/internationalization.md)  
 Décrit la prise en charge internationale dans la bibliothèque Runtime C.  
  
 [Exemples internationaux](http://msdn.microsoft.com/aa8d390c-cf4c-4dd8-9dea-74d81f93f2f8)  
 Fournit des liens vers des exemples illustrant l’internationalisation dans Visual C++.  
  
 [Chaînes de langue et de pays/région](../c-runtime-library/locale-names-languages-and-country-region-strings.md)  
 Fournit les chaînes de langue et de pays/région dans la bibliothèque Runtime C.