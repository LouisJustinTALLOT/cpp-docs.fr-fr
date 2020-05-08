---
title: localeconv
ms.date: 4/2/2020
api_name:
- localeconv
- _o_localeconv
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- localeconv
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
ms.openlocfilehash: c154af87f135f5bf119de26ea8cd0be545ed5382
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916407"
---
# <a name="localeconv"></a>localeconv

Obtient des informations détaillées sur les paramètres régionaux.

## <a name="syntax"></a>Syntaxe

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Valeur de retour

**localeconv** retourne un pointeur vers un objet rempli de type [struct lconv](../../c-runtime-library/standard-types.md). Les valeurs contenues dans l’objet sont copiées à partir des paramètres régionaux dans le stockage local des threads et peuvent être remplacées par les appels suivants à **localeconv**. Les modifications apportées aux valeurs de cet objet ne modifient pas les paramètres régionaux. Les appels à [setlocale](setlocale-wsetlocale.md) avec les valeurs de *catégorie* de **LC_ALL**, **LC_MONETARY**ou **LC_NUMERIC** remplacent le contenu de la structure.

## <a name="remarks"></a>Notes 

La fonction **localeconv** obtient des informations détaillées sur la mise en forme numérique pour les paramètres régionaux actuels. Ces informations sont stockées dans une structure de type **lconv**. La structure **lconv**, définie dans LOCALE.H, contient les membres suivants :

|Champ|Signification|
|-|-|
decimal_point,<br/>_W_decimal_point|Pointeur vers le caractère de virgule décimale pour les quantités non monétaires.
thousands_sep,<br/>_W_thousands_sep|Pointeur vers un caractère qui sépare les groupes de chiffres à gauche de la virgule décimale pour les quantités non monétaires.
regroupement|Pointeur vers un entier de taille **char**qui contient la taille de chaque groupe de chiffres en quantités non monétaires.
int_curr_symbol,<br/>_W_int_curr_symbol|Pointeur vers le symbole monétaire international pour les paramètres régionaux actuels. Les trois premiers caractères spécifient le symbole monétaire international alphabétique tel que le définit la *norme ISO 4217 sur les codes de représentation des monnaies et des fonds*. Le quatrième caractère (situé juste avant le caractère Null) sépare le symbole monétaire international de la quantité monétaire.
currency_symbol,<br/>_W_currency_symbol|Pointeur vers le symbole monétaire local pour les paramètres régionaux actuels.
mon_decimal_point,<br/>_W_mon_decimal_point|Pointeur vers le caractère de virgule décimale pour les quantités monétaires.
mon_thousands_sep,<br/>_W_mon_thousands_sep|Pointeur vers le séparateur pour les groupes de chiffres à gauche de la décimale dans les quantités monétaires.
mon_grouping|Pointeur vers un entier de taille **char**qui contient la taille de chaque groupe de chiffres en quantités monétaires.
positive_sign,<br/>_W_positive_sign|Chaîne indiquant le signe des quantités monétaires non négatives.
negative_sign,<br/>_W_negative_sign|Chaîne indiquant le signe des quantités monétaires négatives.
int_frac_digits|Nombre de chiffres à droite du séparateur décimal dans les quantités monétaires à la mise en forme internationale.
frac_digits|Nombre de chiffres à droite du séparateur décimal dans les quantités monétaires mises en forme.
p_cs_precedes|Défini sur 1 si le symbole monétaire précède la valeur pour une quantité monétaire mise en forme non négative. Défini sur 0 si le symbole suit la valeur.
p_sep_by_space|Défini sur 1 si le symbole monétaire est séparé par un espace de la valeur dans le cas d’une quantité monétaire mise en forme non négative. Défini sur 0 s’il n’y a aucun espace de séparation.
n_cs_precedes|Défini sur 1 si le symbole monétaire précède la valeur dans le cas d’une quantité monétaire mise en forme négative. Défini sur 0 si le symbole suit la valeur.
n_sep_by_space|Défini sur 1 si le symbole monétaire est séparé par un espace de la valeur dans le cas d’une quantité monétaire mise en forme négative. Défini sur 0 s’il n’y a aucun espace de séparation.
p_sign_posn|Position du signe positif dans les quantités monétaires mises en forme non négatives.
n_sign_posn|Position du signe positif dans les quantités monétaires mises en forme négatives.

Sauf indication contraire, les membres de la structure **lconv** qui `char *` ont `wchar_t *` des versions et sont des pointeurs vers des chaînes. L’un de ces qui est égal à **""** (ou **L ""** pour **wchar_t** <strong>\*</strong>) est de longueur nulle ou n’est pas pris en charge dans les paramètres régionaux actuels. Notez que **decimal_point** et **_W_decimal_point** sont toujours pris en charge et de longueur différente de zéro.

Les membres **char** de la structure sont de petits nombres non négatifs, et non des caractères. Si l’un d’eux est égal à **CHAR_MAX**, il n’est pas pris en charge dans les paramètres régionaux actuels.

Les valeurs de **GROUPING** et **mon_grouping** sont interprétées selon les règles suivantes :

- **CHAR_MAX** -ne pas effectuer de regroupement supplémentaire.

- 0-utiliser l’élément précédent pour chacun des chiffres restants.

- *n* -nombre de chiffres qui composent le groupe actuel. L’élément suivant est examiné pour déterminer la taille du groupe de chiffres suivant situé avant le groupe actuel.

Les valeurs de **int_curr_symbol** sont interprétées selon les règles suivantes :

- Les trois premiers caractères spécifient le symbole monétaire international alphabétique tel que le définit la *norme ISO 4217 sur les codes de représentation des monnaies et des fonds*.

- Le quatrième caractère (situé juste avant le caractère Null) sépare le symbole monétaire international de la quantité monétaire.

Les valeurs de **p_cs_precedes** et **n_cs_precedes** sont interprétées selon les règles suivantes (la règle **n_cs_precedes** figure entre parenthèses) :

- 0-le symbole monétaire suit la valeur de la valeur monétaire non négative (négative).

- 1-le symbole monétaire précède la valeur pour la valeur monétaire non négative (négative).

Les valeurs de **p_sep_by_space** et **n_sep_by_space** sont interprétées selon les règles suivantes (la règle **n_sep_by_space** figure entre parenthèses) :

- 0-le symbole monétaire est séparé de la valeur par espace pour une valeur monétaire non négative (négative).

- 1-il n’y a pas de séparation d’espace entre le symbole monétaire et la valeur pour la valeur monétaire non négative (négative).

Les valeurs de **p_sign_posn** et **n_sign_posn** sont interprétées selon les règles suivantes :

- 0-les parenthèses entourent le symbole de quantité et de devise.

- 1-la chaîne de signe précède le symbole de quantité et de devise.

- 2-la chaîne de signe suit la quantité et le symbole monétaire.

- 3-la chaîne de signe précède immédiatement le symbole monétaire.

- 4-le signe de la chaîne suit immédiatement le symbole monétaire.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll, fonctions](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
