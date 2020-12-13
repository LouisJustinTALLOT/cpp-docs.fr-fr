---
description: En savoir plus sur les stratégies d’internationalisation
title: Stratégies d'internationalisation
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- language-portable code [C++]
- MBCS [C++], internationalization strategies
- Windows API [C++], international programming strategies
- Win32 [C++], international programming strategies
- Unicode [C++], globalizing applications
- character sets [C++], international programming strategies
- localization [C++], character sets
ms.assetid: b09d9854-0709-4b9a-a00c-b0b8bc4199b1
ms.openlocfilehash: 51570a3e340a8af0a9f16f8212aa11f6bf3119b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331176"
---
# <a name="internationalization-strategies"></a>Stratégies d'internationalisation

En fonction de vos systèmes d’exploitation et marchés cibles, vous avez plusieurs stratégies d’internationalisation :

- Votre application utilise Unicode.

   Vous utilisez les fonctionnalités spécifiques à Unicode et tous les caractères sont en largeur de 16 bits (même si vous pouvez utiliser des caractères ANSI dans certaines parties de votre programme à des fins particulières). La bibliothèque Runtime C fournit des fonctions, des macros et des types de données pour la programmation Unicode uniquement. MFC est entièrement compatible Unicode.

- Votre application utilise MBCS et peut être exécutée sur n’importe quelle plateforme Win32.

   Vous utilisez les fonctionnalités spécifiques à MBCS. Les chaînes peuvent contenir des caractères codés sur un octet, des caractères codés sur deux octets, ou les deux. La bibliothèque Runtime C fournit des fonctions, des macros et des types de données pour la programmation MBCS uniquement. MFC est entièrement compatible MBCS.

- Le code source de votre application est écrit pour une portabilité totale : en recompilant avec le symbole `_UNICODE` ou le symbole `_MBCS` défini, vous pouvez produire des versions qui utilisent l’une ou l’autre. Pour plus d’informations, consultez [mappages de texte générique dans Tchar. h](../text/generic-text-mappings-in-tchar-h.md).

   Vous utilisez des fonctions, des macros et des types de données Runtime C entièrement portables. La flexibilité de MFC prend en charge l’une de ces stratégies.

Le reste de ces rubriques se concentre sur l’écriture de code entièrement portable que vous pouvez générer en Unicode ou en MBCS.

## <a name="see-also"></a>Voir aussi

[Unicode et MBCS](../text/unicode-and-mbcs.md)<br/>
[Paramètres régionaux et pages de codes](../text/locales-and-code-pages.md)
