---
title: Fonctions de valeur chaîne en valeur numérique | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr80.dll
- msvcr110.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- _tcstoui64
- _tcstoi64
dev_langs:
- C++
helpviewer_keywords:
- parsing, numeric strings
- string conversion, to numeric values
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b65ceb18eb6b8f24db0a85ba2ed13277b13f657
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117495"
---
# <a name="string-to-numeric-value-functions"></a>Fonctions de valeur chaîne en valeur numérique

- [strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)

- [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)

- [strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)

- [_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)

- [_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)

## <a name="remarks"></a>Notes

Chaque fonction de la famille **strtod** convertit une chaîne terminée par Null en une valeur numérique. Les fonctions disponibles sont listées dans le tableau suivant.

|Fonction|Description|
|--------------|-----------------|
|`strtod`|Convertir une chaîne en valeur à virgule flottante double précision|
|`strtol`|Convertir une chaîne en entier long|
|`strtoul`|Convertir une chaîne en entier long non signé|
|`_strtoi64`|Convertir une chaîne en entier `__int64` 64 bits|
|`_strtoui64`|Convertir une chaîne en entier `__int64` non signé 64 bits|

`wcstod`, `wcstol`, `wcstoul` et `_wcstoi64` sont, respectivement, des versions à caractères larges de `strtod`, `strtol`, `strtoul` et `_strtoi64`. L’argument de chaîne de chacune de ces fonctions de caractères larges est une chaîne à caractères larges. Chaque fonction a un comportement identique à celui de son homologue en caractères codés sur un octet.

La fonction `strtod` accepte deux arguments : le premier est la chaîne d’entrée et le second est un pointeur vers le caractère qui termine le processus de conversion. `strtol`, `strtoul`, **_strtoi64** et **_strtoui64** prennent un troisième argument comme base numérique à utiliser dans le processus de conversion.

La chaîne d’entrée est une séquence de caractères qui peut être interprétée comme une valeur numérique du type spécifié. Chaque fonction arrête la lecture de la chaîne au premier caractère qu’il ne peut pas identifier comme faisant partie d’un nombre. Il peut s’agir du caractère Null de fin. Pour `strtol`, `strtoul`, `_strtoi64` et `_strtoui64`, ce caractère de fin peut également être le premier caractère numérique supérieur ou égal à la base numérique fournie par l’utilisateur.

Si le pointeur fourni par l’utilisateur qui pointe vers un caractère de fin de conversion n’est pas défini sur **NULL** au moment de l’appel, un pointeur vers le caractère qui a causé l’arrêt de l’analyse est stocké à sa place. Si aucune conversion ne peut être effectuée (aucun chiffre valide n’a été trouvé ou la base spécifiée n’est pas valide), la valeur du pointeur de chaîne est stockée à cette adresse.

`strtod` attend une chaîne au format suivant :

[*espace blanc*] [*signe*] [`digits`] [**.**`digits`] [ {**d** &#124; **D** &#124; **e** &#124; **E**}[*signe*]`digits`]

Un *espace blanc* peut se composer d’espaces et de tabulations, qui sont ignorés ; un *signe* est un signe plus (**+**) ou moins (**-**) ; et `digits` représente un ou plusieurs chiffres décimaux. Si aucun chiffre n’apparaît avant le caractère de base, il doit en figurer au moins un après le caractère de base. Les chiffres décimaux peuvent être suivis d’un exposant, qui se compose d’une lettre d’introduction (**d**, **D**, **e** ou **E**) et éventuellement d’un entier signé. S’il n’apparaît ni exposant ni caractère de base, il est supposé qu’un caractère de base suit le dernier chiffre dans la chaîne. Le premier caractère qui ne correspond pas à ce format a pour effet d’arrêter l’analyse.

Les fonctions `strtol`, `strtoul`, `_strtoi64` et `_strtoui64` attendent une chaîne au format suivant :

[*espace blanc*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [`digits`]

Si l’argument de base a une valeur comprise entre 2 et 36, elle est utilisée comme base numérique. Si sa valeur est de 0, les caractères initiaux référencés par le pointeur de fin de conversion sont utilisés pour déterminer la base. Si le premier caractère est 0 et que le deuxième est différent de « x » ou « X », la chaîne est interprétée comme étant un entier octal. Sinon, elle est interprétée comme un nombre décimal. Si le premier caractère est « 0 » et que le deuxième est « x » ou « X », la chaîne est interprétée comme étant un entier hexadécimal. Si le premier caractère est un chiffre compris entre « 1 » et « 9 », la chaîne est interprétée comme étant un entier décimal. Les lettres de « a » à « z » (ou de « A » à « Z ») se voient affecter des valeurs comprises entre 10 et 35 ; seules sont autorisées les lettres dont les valeurs affectées sont inférieures à la *base*. `strtoul` et `_strtoui64` autorise la présence d’un signe plus (**+**) ou moins (**-**) en guise de préfixe ; la présence d’un signe moins de début indique que le signe de la valeur de retour est négative.

La valeur de sortie est affectée par la valeur du paramètre de catégorie `LC_NUMERIC` des paramètres régionaux. Pour plus d’informations, consultez [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Les versions de ces fonctions sans le suffixe **_l** utilisent les paramètres régionaux pour ce comportement dépendant des paramètres régionaux ; les versions avec le suffixe **_l** sont identiques, sauf qu’elles utilisent à la place les paramètres régionaux transmis.

Lorsque la valeur retournée par ces fonctions provoque un dépassement de capacité positif ou négatif, ou lorsque la conversion n’est pas possible, des valeurs case spéciales sont retournées, comme indiqué ici :

|Fonction|Condition|Valeur retournée|
|--------------|---------------|--------------------|
|`strtod`|Dépassement|+/- `HUGE_VAL`|
|`strtod`|Dépassement de capacité négatif ou aucune conversion|0|
|`strtol`|+ Dépassement|**LONG_MAX**|
|`strtol`|- Dépassement|**LONG_MIN**|
|`strtol`|Dépassement de capacité négatif ou aucune conversion|0|
|`_strtoi64`|+ Dépassement|**_I64_MAX**|
|`_strtoi64`|- Dépassement|**_I64_MIN**|
|`_strtoi64`|Aucune conversion|0|
|`_strtoui64`|Dépassement|**_UI64_MAX**|
|`_strtoui64`|Aucune conversion|0|

 **_I64_MAX**, _**I64_MIN** et **_UI64_MAX** sont définis dans LIMITS.H.

`wcstod`, `wcstol`, `wcstoul`, `_wcstoi64` et `_wcstoui64` sont des versions à caractères larges de `strtod`, `strtol`, `strtoul`, `_strtoi64` et `_strtoui64`, respectivement ; le pointeur vers un argument de fin de conversion de chacune de ces fonctions de caractères larges est une chaîne à caractères larges. Sinon, chacune de ces fonctions de caractères larges se comporte comme son caractère homologue codé sur un octet.

## <a name="see-also"></a>Voir aussi

[Conversion de données](../c-runtime-library/data-conversion.md)<br/>
[Paramètres régionaux](../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Prise en charge de la virgule flottante](../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)