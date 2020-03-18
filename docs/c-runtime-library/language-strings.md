---
title: Language Strings
ms.date: 11/04/2016
helpviewer_keywords:
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
ms.openlocfilehash: 18a94d33f9ca382bb6c7cd77a4f2b33ed800f2c6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438252"
---
# <a name="language-strings"></a>Language Strings

Les fonctions [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) et [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) peuvent utiliser les langues prises en charge par l’API NLS Windows sur les systèmes d’exploitation qui n’utilisent pas la page de codes Unicode. Pour voir une liste des langues prises en charge par la version du système d’exploitation, consultez [Appendix A: Product Behavior](https://msdn.microsoft.com/library/cc233982.aspx) dans [MS-LCID] : Informations de référence Windows LCID (Language Code Identifier). La chaîne de langue peut être une des valeurs des colonnes **Langue** et **Balise de la langue** de la liste des langues prises en charge. Pour obtenir un exemple de code énumérant les noms de paramètres régionaux disponibles et les valeurs associées, consultez [NLS : exemple d’API en fonction du nom](/windows/win32/intl/nls--name-based-apis-sample).

## <a name="additional-supported-language-strings"></a>Chaînes de langues supplémentaires pris en charge

L’implémentation de la bibliothèque runtime Microsoft C prend également en charge ces chaînes de langue :

|Chaîne de langue|Nom des paramètres régionaux équivalents|
|---------------------|----------------------------|
|américain|fr-FR|
|american english|fr-FR|
|american-english|fr-FR|
|australien|en-AU|
|belge|nl-BE|
|canadien|en-CA|
|chh|zh-HK|
|chi|zh-SG|
|chinois|zh|
|chinese-hongkong|zh-HK|
|chinese-simplified|zh-CN|
|chinese-singapore|zh-SG|
|chinese-traditional|zh-TW|
|dutch-belgian|nl-BE|
|english-american|fr-FR|
|english-aus|en-AU|
|english-belize|en-BZ|
|english-can|en-CA|
|english-caribbean|en-029|
|english-ire|en-IE|
|english-jamaica|en-JM|
|english-nz|en-NZ|
|english-south africa|en-ZA|
|english-trinidad y tobago|en-TT|
|english-uk|en-GB|
|english-us|fr-FR|
|english-usa|fr-FR|
|french-belgian|fr-BE|
|french-canadian|fr-CA|
|french-luxembourg|fr-LU|
|french-swiss|fr-CH|
|german-austrian|de-AT|
|german-lichtenstein|de-LI|
|german-luxembourg|de-LU|
|german-swiss|de-CH|
|irish-english|en-IE|
|italian-swiss|it-CH|
|norvégien|non|
|norwegian-bokmal|nb-NO|
|norwegian-nynorsk|nn-NO|
|portuguese-brazilian|pt-br|
|spanish-argentina|es-AR|
|spanish-bolivia|es-BO|
|spanish-chile|es-CL|
|spanish-colombia|es-CO|
|spanish-costa rica|es-CR|
|spanish-dominican republic|es-DO|
|spanish-ecuador|es-EC|
|spanish-el salvador|es-SV|
|spanish-guatemala|es-GT|
|spanish-honduras|es-HN|
|spanish-mexican|es-MX|
|spanish-modern|es-ES|
|spanish-nicaragua|es-NI|
|spanish-panama|es-PA|
|spanish-paraguay|es-PY|
|spanish-peru|es-PE|
|spanish-puerto rico|es-PR|
|spanish-uruguay|es-UY|
|spanish-venezuela|es-VE|
|swedish-finland|sv-FI|
|suisse|de-CH|
|uk|en-GB|
|us|fr-FR|
|usa|fr-FR|

## <a name="see-also"></a>Voir aussi

[Chaînes relatives aux noms des paramètres régionaux, aux langues et au pays/à la région](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Country/Region Strings](../c-runtime-library/country-region-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
