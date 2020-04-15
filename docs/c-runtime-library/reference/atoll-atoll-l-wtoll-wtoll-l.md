---
title: atoll, _atoll_l, _wtoll, _wtoll_l
ms.date: 4/2/2020
api_name:
- _wtoll
- _atoll_l
- _wtoll_l
- atoll
- _o__atoll_l
- _o__wtoll
- _o__wtoll_l
- _o_atoll
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tstoll_l
- _wtoll
- _atoll_l
- _ttoll
- _tstoll
- _wtoll_l
- atoll
helpviewer_keywords:
- atoll function
- _wtoll_l function
- _wtoll function
- _atoll_l function
ms.assetid: 5e85fcac-b351-4882-bff2-6e7c469b7fa8
ms.openlocfilehash: 34b7d0fdedb55241452f9a7f9937b64c58f7772c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348713"
---
# <a name="atoll-_atoll_l-_wtoll-_wtoll_l"></a>atoll, _atoll_l, _wtoll, _wtoll_l

Convertit une corde **long** **en** une longue integer longue.

## <a name="syntax"></a>Syntaxe

```C
long long atoll(
   const char *str
);
long long _wtoll(
   const wchar_t *str
);
long long _atoll_l(
   const char *str,
   _locale_t locale
);
long long _wtoll_l(
   const wchar_t *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*Str*<br/>
Chaîne à convertir.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chaque fonction renvoie la **longue** **valeur** produite en interprétant les caractères d’entrée comme un nombre. La valeur de retour pour **l’atoll** est de 0 si l’entrée ne peut pas être convertie en une valeur de ce type.

Pour le débordement de grandes valeurs intégrales positives, les rendements **de l’atoll** **LLONG_MAX**, et pour le débordement de grandes valeurs intégrales négatives, il revient **LLONG_MIN**.

Dans tous les cas hors de portée, **errno** est réglé sur **ERANGE**. Si le paramètre qui est passé est **NULL**, le gestionnaire de paramètres invalides est invoqué, tel que décrit dans [la validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions **définies errno** à **EINVAL** et retour 0.

## <a name="remarks"></a>Notes

Ces fonctions convertissent une chaîne de caractères **en** une **longue** valeur d’intégrage.

La chaîne d’entrée est une séquence de caractères qui peut être interprétée comme une valeur numérique du type spécifié. La fonction arrête de lire la chaîne d’entrée au premier caractère qu’elle ne peut pas reconnaître comme faisant partie d’un nombre. Ce caractère peut être le caractère null ('\0' ou L'\0') qui termine la chaîne.

*L’argument de* l’atoll a la forme suivante : **atoll**

> [*espace blanc*] [*signe*] [*chiffres*]

Un *espace blanc* se compose de caractères d’espace ou d’onglet, qui sont ignorés ; *signe* est soit plus () ou moins (-); et *les chiffres* sont un ou plusieurs chiffres.

**_wtoll** est identique à **l’atoll,** sauf qu’il faut une large chaîne de caractère comme paramètre.

Les versions de ces fonctions qui ont le **suffixe _l** sont identiques aux versions qui ne l’ont pas, sauf qu’ils utilisent le paramètre local qui est passé au lieu de la localisation actuelle. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tstoll**|**atoll**|**atoll**|**_wtoll**|
|**_tstoll_l**|**_atoll_l**|**_atoll_l**|**_wtoll_l**|
|**_ttoll**|**_atoll**|**_atoll**|**_wtoll**|

## <a name="requirements"></a>Spécifications

|Routines|En-tête requis|
|--------------|---------------------|
|**atoll**, **_atoll_l**|\<stdlib.h>|
|**_wtoll**, **_wtoll_l**|\<stdlib.h> ou \<wchar.h>|

## <a name="example"></a>Exemple

Ce programme montre comment utiliser les fonctions **atoll** pour convertir les numéros stockés sous forme de chaînes en valeurs numériques.

```C
// crt_atoll.c
// Build with: cl /W4 /Tc crt_atoll.c
// This program shows how to use the atoll
// functions to convert numbers stored as
// strings to numeric values.
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main(void)
{
    char *str = NULL;
    long long value = 0;

    // An example of the atoll function
    // with leading and trailing white spaces.
    str = "  -27182818284 ";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);

    // Another example of the atoll function
    // with an arbitrary decimal point.
    str = "314127.64";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);

    // Another example of the atoll function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: atoll("  -27182818284 ") = -27182818284
Function: atoll("314127.64") = 314127
Function: atoll("3336402735171707160320") = 9223372036854775807
Overflow condition occurred.
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
