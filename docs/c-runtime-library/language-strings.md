---
title: Language Strings
description: 'En savoir plus sur : chaînes de langage'
ms.date: 1/12/2021
helpviewer_keywords:
- language strings
ms.openlocfilehash: ec82bb8b9efb9c366c287c79b71b60a3c6bc6ab2
ms.sourcegitcommit: b51f79b5394e12cd90cb65c85cc01716f90bfc90
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98167019"
---
# <a name="language-strings"></a>Language Strings

Les [`setlocale`](../c-runtime-library/reference/setlocale-wsetlocale.md) [`_create_locale`](../c-runtime-library/reference/create-locale-wcreate-locale.md) fonctions et peuvent utiliser les langues prises en charge de l’API nls Windows sur les systèmes d’exploitation qui n’utilisent pas la page de codes Unicode. Pour obtenir la liste des langues prises en charge par la version du système d’exploitation, voir [annexe a : comportement du produit](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c) en \[ MS-LCID] : référence LCID (Language code identifier) Windows. La chaîne de langue peut être une des valeurs des colonnes **Langue** et **Balise de la langue** de la liste des langues prises en charge. Pour obtenir un exemple de code qui énumère les noms de paramètres régionaux disponibles et les valeurs associées, consultez [exemple d’API nls : basée sur un nom](/windows/win32/intl/nls--name-based-apis-sample).

## <a name="supported-language-strings"></a>Chaînes de langue prises en charge

L’implémentation de la bibliothèque runtime Microsoft C prend également en charge ces chaînes de langue :

|Chaîne de langue|Nom des paramètres régionaux équivalents|
|---------------------|----------------------------|
|`american`|`en-US`|
|`american english`|`en-US`|
|`american-english`|`en-US`|
|`australian`|`en-AU`|
|`belgian`|`nl-BE`|
|`canadian`|`en-CA`|
|`chh`|`zh-HK`|
|`chi`|`zh-SG`|
|`chinese`|`zh`|
|`chinese-hongkong`|`zh-HK`|
|`chinese-simplified`|`zh-CN`|
|`chinese-singapore`|`zh-SG`|
|`chinese-traditional`|`zh-TW`|
|`dutch-belgian`|`nl-BE`|
|`english-american`|`en-US`|
|`english-aus`|`en-AU`|
|`english-belize`|`en-BZ`|
|`english-can`|`en-CA`|
|`english-caribbean`|`en-029`|
|`english-ire`|`en-IE`|
|`english-jamaica`|`en-JM`|
|`english-nz`|`en-NZ`|
|`english-south africa`|`en-ZA`|
|`english-trinidad y tobago`|`en-TT`|
|`english-uk`|`en-GB`|
|`english-us`|`en-US`|
|`english-usa`|`en-US`|
|`french-belgian`|`fr-BE`|
|`french-canadian`|`fr-CA`|
|`french-luxembourg`|`fr-LU`|
|`french-swiss`|`fr-CH`|
|`german-austrian`|`de-AT`|
|`german-lichtenstein`|`de-LI`|
|`german-luxembourg`|`de-LU`|
|`german-swiss`|`de-CH`|
|`irish-english`|`en-IE`|
|`italian-swiss`|`it-CH`|
|`norwegian`|`no`|
|`norwegian-bokmal`|`nb-NO`|
|`norwegian-nynorsk`|`nn-NO`|
|`portuguese-brazilian`|`pt-BR`|
|`spanish-argentina`|`es-AR`|
|`spanish-bolivia`|`es-BO`|
|`spanish-chile`|`es-CL`|
|`spanish-colombia`|`es-CO`|
|`spanish-costa rica`|`es-CR`|
|`spanish-dominican republic`|`es-DO`|
|`spanish-ecuador`|`es-EC`|
|`spanish-el salvador`|`es-SV`|
|`spanish-guatemala`|`es-GT`|
|`spanish-honduras`|`es-HN`|
|`spanish-mexican`|`es-MX`|
|`spanish-modern`|`es-ES`|
|`spanish-nicaragua`|`es-NI`|
|`spanish-panama`|`es-PA`|
|`spanish-paraguay`|`es-PY`|
|`spanish-peru`|`es-PE`|
|`spanish-puerto rico`|`es-PR`|
|`spanish-uruguay`|`es-UY`|
|`spanish-venezuela`|`es-VE`|
|`swedish-finland`|`sv-FI`|
|`swiss`|`de-CH`|
|`uk`|`en-GB`|
|`us`|`en-US`|
|`usa`|`en-US`|

## <a name="see-also"></a>Voir aussi

- [Chaînes de noms de paramètres régionaux, de langues et de pays/région](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
- [Chaînes pays/région](../c-runtime-library/country-region-strings.md)\
- [`setlocale`, `_wsetlocale`](../c-runtime-library/reference/setlocale-wsetlocale.md)\
- [`_create_locale`, `_wcreate_locale`](../c-runtime-library/reference/create-locale-wcreate-locale.md)
