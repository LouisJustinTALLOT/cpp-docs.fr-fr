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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a617980d60b3a12c06b30aab6cd457792a1aa770
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342142"
---
# <a name="localeconv"></a>localeconv

Obtient des informations détaillées sur les paramètres régionaux.

## <a name="syntax"></a>Syntaxe

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Valeur de retour

**localconv** retourne un pointeur à un objet rempli de type [struct lconv](../../c-runtime-library/standard-types.md). Les valeurs contenues dans l’objet sont copiées à partir des paramètres locaux dans le stockage thread-local, et peuvent être écrasées par des appels ultérieurs à **localconv**. Les modifications apportées aux valeurs de cet objet ne modifient pas les paramètres locaux. Appels à [setlocale](setlocale-wsetlocale.md) avec des valeurs de *catégorie* de **LC_ALL**, **LC_MONETARY**, ou **LC_NUMERIC** de remplacer le contenu de la structure.

## <a name="remarks"></a>Notes

La fonction **localconv** obtient des informations détaillées sur le formatage numérique pour le lieu actuel. Ces informations sont stockées dans une structure de type **lconv**. La structure **lconv**, définie dans LOCALE.H, contient les membres suivants :

|Champ|Signification|
|-|-|
decimal_point,<br/>_W_decimal_point|Pointeur au caractère décimal-point pour les quantités non peu matrimariaires.
thousands_sep,<br/>_W_thousands_sep|Pointeur au caractère qui sépare les groupes de chiffres à gauche du point décimal pour les quantités non peu matrimariaires.
regroupement|Pointeur vers un intégrier de taille **char**qui contient la taille de chaque groupe de chiffres en quantités non matétaires.
int_curr_symbol,<br/>_W_int_curr_symbol|Pointeur vers le symbole de devise internationale pour le lieu actuel. Les trois premiers caractères spécifient le symbole monétaire international alphabétique tel que le définit la *norme ISO 4217 sur les codes de représentation des monnaies et des fonds*. Le quatrième caractère (situé juste avant le caractère Null) sépare le symbole monétaire international de la quantité monétaire.
currency_symbol,<br/>_W_currency_symbol|Pointeur vers le symbole de monnaie locale pour le local actuel.
mon_decimal_point,<br/>_W_mon_decimal_point|Pointeur au caractère décimal-point pour les quantités monétaires.
mon_thousands_sep,<br/>_W_mon_thousands_sep|Pointeur à séparateur pour les groupes de chiffres à gauche de la place décimale en quantités monétaires.
mon_grouping|Pointeur vers un intégrisé de taille **char**qui contient la taille de chaque groupe de chiffres en quantités monétaires.
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

Sauf comme indiqué, les membres de `char *` la `wchar_t *` structure **lconv** qui ont et les versions sont des pointeurs aux cordes. L’un de ces qui égale **""** (ou **L"** pour **wchar_t** <strong>\*</strong>) est soit de longueur zéro ou non pris en charge dans le lieu actuel. Notez que **decimal_point** et **_W_decimal_point** sont toujours pris en charge et de longueur non zéro.

Les membres de **l’omble chevalier** de la structure sont de petits nombres non natifs, pas des caractères. Si l’un d’eux est égal à **CHAR_MAX**, il n’est pas pris en charge dans les paramètres régionaux actuels.

Les valeurs de **regroupement** et **de mon_grouping** sont interprétées selon les règles suivantes :

- **CHAR_MAX** - N’effectuez aucun autre regroupement.

- 0 - Utilisez l’élément précédent pour chacun des chiffres restants.

- *n* - Nombre de chiffres qui composent le groupe actuel. L’élément suivant est examiné pour déterminer la taille du groupe de chiffres suivant situé avant le groupe actuel.

Les valeurs de **int_curr_symbol** sont interprétées selon les règles suivantes :

- Les trois premiers caractères spécifient le symbole monétaire international alphabétique tel que le définit la *norme ISO 4217 sur les codes de représentation des monnaies et des fonds*.

- Le quatrième caractère (situé juste avant le caractère Null) sépare le symbole monétaire international de la quantité monétaire.

Les valeurs de **p_cs_precedes** et **n_cs_precedes** sont interprétées selon les règles suivantes (la règle **n_cs_precedes** figure entre parenthèses) :

- 0 - Le symbole de devise suit la valeur pour la valeur monétaire non native (négative).

- 1 - Le symbole de devise précède la valeur pour la valeur monétaire non native (négative).

Les valeurs de **p_sep_by_space** et **n_sep_by_space** sont interprétées selon les règles suivantes (la règle **n_sep_by_space** figure entre parenthèses) :

- 0 - Le symbole de devise est séparé de la valeur par espace pour la valeur monétaire non native (négative).

- 1 - Il n’y a pas de séparation de l’espace entre le symbole de change et la valeur pour la valeur monétaire non native (négative).

Les valeurs de **p_sign_posn** et **n_sign_posn** sont interprétées selon les règles suivantes :

- 0 - Parenthèses entourent la quantité et le symbole de la monnaie.

- 1 - La chaîne de signe précède la quantité et le symbole de devise.

- 2 - La chaîne de signe suit la quantité et le symbole de devise.

- 3 - La chaîne de signalisation précède immédiatement le symbole de la monnaie.

- 4 - La chaîne de signe suit immédiatement le symbole de devise.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Local](../../c-runtime-library/locale.md)<br/>
[setlocale setlocale setlocale setloc](../../preprocessor/setlocale.md)<br/>
[fonctions strcoll](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
