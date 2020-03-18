---
title: Chaînes de pays-région
ms.date: 11/04/2016
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: 8556e005618a1b69c47498a07e218284dcb1164f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443434"
---
# <a name="countryregion-strings"></a>Country/Region Strings

Les chaînes de pays et de région peuvent être combinés avec une chaîne de langue pour créer une spécification de paramètres régionaux pour les fonctions `setlocale`, `_wsetlocale`, `_create_locale`et `_wcreate_locale` . Pour obtenir des listes des noms de pays et de régions pris en charge par différentes versions du système d’exploitation Windows, consultez les colonnes **Langue**, **Emplacement** et **Balise de langue** de la table dans [Appendix A: Product Behavior](https://msdn.microsoft.com/library/cc233982.aspx) dans [MS-LCID] : référence d’identificateur de code de langue (LCID) Windows. Pour obtenir un exemple de code énumérant les noms de paramètres régionaux disponibles et les valeurs associées, consultez [NLS : exemple d’API en fonction du nom](/windows/win32/intl/nls--name-based-apis-sample).

## <a name="additional-supported-country-and-region-strings"></a>Chaînes de pays et de région supplémentaires prises en charge

L’implémentation de la bibliothèque runtime Microsoft C prend également en charge les chaînes et abréviations de pays/région supplémentaires suivantes :

|Chaîne de pays/région|Abréviation|Nom des paramètres régionaux équivalents|
|----------------------------|------------------|----------------------------|
|america|États-Unis|fr-FR|
|britain|GBR|en-GB|
|china|CHN|zh-CN|
|tchèque|CZE|cs-CZ|
|england|GBR|en-GB|
|great britain|GBR|en-GB|
|holland|NLD|nl-NL|
|hong-kong|HKG|zh-HK|
|new-zealand|NZL|en-NZ|
|nz|NZL|en-NZ|
|pr china|CHN|zh-CN|
|pr-china|CHN|zh-CN|
|puerto-rico|PRI|es-PR|
|slovaque|SVK|sk-SK|
|south africa|ZAF|af-ZA|
|south korea|KOR|ko-KR|
|south-africa|ZAF|af-ZA|
|south-korea|KOR|ko-KR|
|trinidad & tobago|TTO|en-TT|
|uk|GBR|en-GB|
|united-kingdom|GBR|en-GB|
|united-states|États-Unis|fr-FR|
|us|États-Unis|fr-FR|

## <a name="see-also"></a>Voir aussi

[Chaînes relatives aux noms des paramètres régionaux, aux langues et au pays/à la région](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Chaînes de langue](../c-runtime-library/language-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
