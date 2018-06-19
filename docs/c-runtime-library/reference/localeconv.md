---
title: localeconv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- localeconv
apilocation:
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
apitype: DLLExport
f1_keywords:
- localeconv
dev_langs:
- C++
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe3cc75430dfa9bb2f4c5513f4b2ba5a2fd1c4c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405248"
---
# <a name="localeconv"></a>localeconv

Obtient des informations détaillées sur les paramètres régionaux.

## <a name="syntax"></a>Syntaxe

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Valeur de retour

**localeconv** retourne un pointeur vers un objet rempli de type [struct lconv](../../c-runtime-library/standard-types.md). Les valeurs contenues dans l’objet sont copiées depuis les paramètres régionaux dans le stockage local des threads et peut être remplacées par les appels suivants à **localeconv**. Modifications apportées aux valeurs dans cet objet ne modifiez pas les paramètres régionaux. Les appels à [setlocale](setlocale-wsetlocale.md) avec *catégorie* les valeurs de **LC_ALL**, **LC_MONETARY**, ou **LC_NUMERIC** remplacer le contenu de la structure.

## <a name="remarks"></a>Notes

Le **localeconv** fonction obtient des informations détaillées sur la mise en forme numérique pour les paramètres régionaux actuels. Ces informations sont stockées dans une structure de type **lconv**. La structure **lconv**, définie dans LOCALE.H, contient les membres suivants :

|Champ|Signification|
|-|-|
decimal_point,<br/>_W_decimal_point|Pointeur vers caractère pour les quantités non monétaires de virgule décimale.
thousands_sep,<br/>_W_thousands_sep|Pointeur vers le caractère qui sépare les groupes de chiffres à gauche de la virgule décimale pour les quantités non monétaires.
regroupement|Pointeur vers un **char**-taille d’entier qui contient la taille de chaque groupe de chiffres dans les quantités non monétaires.
int_curr_symbol,<br/>_W_int_curr_symbol|Pointeur vers le symbole monétaire international pour les paramètres régionaux actuels. Les trois premiers caractères spécifient le symbole monétaire international alphabétique tel que le définit la *norme ISO 4217 sur les codes de représentation des monnaies et des fonds*. Le quatrième caractère (situé juste avant le caractère Null) sépare le symbole monétaire international de la quantité monétaire.
currency_symbol,<br/>_W_currency_symbol|Pointeur vers le symbole de devise pour les paramètres régionaux actuels.
mon_decimal_point,<br/>_W_mon_decimal_point|Pointeur vers caractère pour les quantités monétaires de virgule décimale.
mon_thousands_sep,<br/>_W_mon_thousands_sep|Pointeur vers le séparateur de groupes de chiffres à gauche du séparateur décimal dans les quantités monétaires.
mon_grouping|Pointeur vers un **char**-taille d’entier qui contient la taille de chaque groupe de chiffres dans les quantités monétaires.
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

Sauf les membres spécifiés, de la **lconv** structure qui ont `char *` et `wchar_t *` versions sont des pointeurs vers des chaînes. Toutes ces égal à **» «** (ou **L » «** pour **wchar_t \*** ) est de longueur nulle ou non pris en charge dans les paramètres régionaux actuels. Notez que **decimal_point** et **_W_decimal_point** sont toujours prises en charge et de longueur différente de zéro.

Le **char** membres de la structure sont de petits nombres non négatifs, pas de caractères. Si l’un d’eux est égal à **CHAR_MAX**, il n’est pas pris en charge dans les paramètres régionaux actuels.

Les valeurs de **regroupement** et **mon_grouping** sont interprétés en fonction des règles suivantes :

- **CHAR_MAX** -n’effectuent pas de n’importe quel regroupement.

- 0 - utilisez l’élément précédent pour chacun des autres chiffres.

- *n* -nombre de chiffres qui composent le groupe actuel. L’élément suivant est examiné pour déterminer la taille du groupe de chiffres suivant situé avant le groupe actuel.

Les valeurs de **int_curr_symbol** sont interprétées selon les règles suivantes :

- Les trois premiers caractères spécifient le symbole monétaire international alphabétique tel que le définit la *norme ISO 4217 sur les codes de représentation des monnaies et des fonds*.

- Le quatrième caractère (situé juste avant le caractère Null) sépare le symbole monétaire international de la quantité monétaire.

Les valeurs de **p_cs_precedes** et **n_cs_precedes** sont interprétées selon les règles suivantes (la règle **n_cs_precedes** figure entre parenthèses) :

- 0 - symbole monétaire suit la valeur pour une valeur non négative (négatif) au format monétaire.

- 1 - symbole précède la valeur pour une valeur non négative (négatif) au format monétaire.

Les valeurs de **p_sep_by_space** et **n_sep_by_space** sont interprétées selon les règles suivantes (la règle **n_sep_by_space** figure entre parenthèses) :

- 0 - symbole monétaire est séparée de la valeur par un espace de valeur non négative (négatif) au format monétaire.

- 1 - il n’existe pas d’espace de séparation entre symbole monétaire et la valeur de la valeur non négative (négatif) au format monétaire.

Les valeurs de **p_sign_posn** et **n_sign_posn** sont interprétées selon les règles suivantes :

- 0 - parenthèses entourent symbole quantité et de devise.

- 1 - chaîne de connexion précède le symbole de quantité et de devise.

- 2 - chaîne de connexion suit le symbole de quantité et de devise.

- 3 - chaîne de connexion précède immédiatement le symbole monétaire.

- 4 - signe de chaîne symbole suit immédiatement.

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
