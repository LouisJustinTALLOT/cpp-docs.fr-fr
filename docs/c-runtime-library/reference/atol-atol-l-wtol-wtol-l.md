---
title: atol, _atol_l, _wtol, _wtol_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- atol
- _wtol_l
- _wtol
- _atol_l
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _atol_l
- _ttol_l
- _tstol_l
- _tstol
- _wtol
- _ttol
- _wtol_l
dev_langs:
- C++
helpviewer_keywords:
- tstol function
- atol function
- ttol function
- _atol_l function
- _tstol_l function
- string conversion, to integers
- _tstol function
- _ttol function
- _ttol_l function
- atol_l function
- wtol_l function
- _wtol_l function
- wtol function
- _wtol function
ms.assetid: cedfc21c-2d64-4e9c-bd04-bdf60b12db46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: deb23d856fc0ec5aecfdb726256394d5135a18d4
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450704"
---
# <a name="atol-atoll-wtol-wtoll"></a>atol, _atol_l, _wtol, _wtol_l

Convertissent une chaîne en un entier long.

## <a name="syntax"></a>Syntaxe

```C
long atol(
   const char *str
);
long _atol_l(
   const char *str,
   _locale_t locale
);
long _wtol(
   const wchar_t *str
);
long _wtol_l(
   const wchar_t *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Chaîne à convertir.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chaque fonction retourne le **long** valeur produite par l’interprétation des caractères d’entrée en tant que nombre. La valeur de retour est 0L pour **atol** si l’entrée ne peut pas être convertie en valeur de ce type.

Dans le cas de dépassement de capacité avec grandes valeurs intégrales positifs, **atol** retourne **LONG_MAX**; dans le cas de dépassement de capacité avec grandes valeurs intégrales négatifs, **LONG_MIN** est retourné. Dans tous les cas d’out-of-range, **errno** a la valeur **ERANGE**. Si le paramètre passé est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL** et retourne 0.

## <a name="remarks"></a>Notes

Ces fonctions convertissent une chaîne de caractères en une valeur d’entier long (**atol**).

La chaîne d’entrée est une séquence de caractères qui peut être interprétée comme une valeur numérique du type spécifié. La fonction arrête de lire la chaîne d’entrée au premier caractère qu’elle ne peut pas reconnaître comme faisant partie d’un nombre. Ce caractère peut être le caractère Null ('\0' ou L'\0') terminant la chaîne.

Le *str* argument **atol** a la forme suivante :

> [*espace blanc*] [*signe*] [*chiffres*]]

A *espace blanc* se compose de caractères espace ou tabulation, qui sont ignorés ; *signe* est plus (+) ou moins (-) ; et *chiffres* sont un ou plusieurs chiffres.

**_wtol** est identique à **atol** sauf qu’elle prend une chaîne de caractères larges.

Les versions de ces fonctions avec le **_l** suffixe sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux actuels. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstol**|**atol**|**atol**|**_wtol**|
|**_ttol**|**atol**|**atol**|**_wtol**|

## <a name="requirements"></a>Spécifications

|Routines|En-tête requis|
|--------------|---------------------|
|**atol**|\<stdlib.h>|
|**_atol_l**, **_wtol**, **_wtol_l**|\<stdlib.h> et \<wchar.h>|

## <a name="example"></a>Exemple

Ce programme montre comment les nombres stockés sous forme de chaînes peuvent être converties en valeurs numériques à l’aide de la **atol** (fonction).

```C
// crt_atol.c
// This program shows how numbers stored as
// strings can be converted to numeric values
// using the atol functions.
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
    char    *str = NULL;
    long    value = 0;

    // An example of the atol function
    // with leading and trailing white spaces.
    str = "  -2309 ";
    value = atol( str );
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );

    // Another example of the atol function
    // with an arbitrary decimal point.
    str = "314127.64";
    value = atol( str );
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );

    // Another example of the atol function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = atol( str );
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: atol( "  -2309 " ) = -2309
Function: atol( "314127.64" ) = 314127
Function: atol( "3336402735171707160320" ) = 2147483647
Overflow condition occurred.
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
