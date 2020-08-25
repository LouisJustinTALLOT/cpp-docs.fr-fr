---
title: Chaînes de pays-région
ms.date: 11/04/2016
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: d5d8c10e30886c1b34bb5dc95296bc594acda1a4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831851"
---
# <a name="countryregion-strings"></a>chaînes pays/région

Les chaînes de pays et de région peuvent être combinés avec une chaîne de langue pour créer une spécification de paramètres régionaux pour les fonctions `setlocale`, `_wsetlocale`, `_create_locale`et `_wcreate_locale` . Pour obtenir la liste des noms de pays et de région pris en charge par les différentes versions de système d’exploitation Windows, consultez les colonnes **langue**, **emplacement**et **balise de langue** du tableau de l' [annexe A : comportement du produit](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c) dans \[ MS-LCID] : référence LCID (Language code identifier) Windows. Pour obtenir un exemple de code énumérant les noms de paramètres régionaux disponibles et les valeurs associées, consultez [NLS : exemple d’API en fonction du nom](/windows/win32/intl/nls--name-based-apis-sample).

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

[Chaînes de noms de paramètres régionaux, de langues et de pays/région](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Chaînes de langue](../c-runtime-library/language-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
