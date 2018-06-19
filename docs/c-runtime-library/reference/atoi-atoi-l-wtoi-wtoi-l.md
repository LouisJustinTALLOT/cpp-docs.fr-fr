---
title: atoi, _atoi_l, _wtoi, _wtoi_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wtoi
- _wtoi_l
- atoi
- _atoi_l
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
- _tstoi
- _wtoi
- _ttoi
- atoi
- _atoi_l
- _wtoi_l
dev_langs:
- C++
helpviewer_keywords:
- _atoi_l function
- ttoi function
- atoi_l function
- string conversion, to integers
- _wtoi function
- wtoi_l function
- tstoi function
- _ttoi function
- _tstoi function
- _wtoi_l function
- atoi function
- wtoi function
ms.assetid: ad7fda30-28ab-421f-aaad-ef0b8868663a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ec426518aed278f98ca334ba4ed34830f5836a1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397153"
---
# <a name="atoi-atoil-wtoi-wtoil"></a>atoi, _atoi_l, _wtoi, _wtoi_l

Convertissent une chaîne en entier.

## <a name="syntax"></a>Syntaxe

```C
int atoi(
   const char *str
);
int _wtoi(
   const wchar_t *str
);
int _atoi_l(
   const char *str,
   _locale_t locale
);
int _wtoi_l(
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

Chaque fonction retourne le **int** valeur produite par l’interprétation des caractères d’entrée en tant que nombre. La valeur de retour est 0 pour **atoi** et **_wtoi**, si l’entrée ne peut pas être convertie en valeur de ce type.

Dans le cas de dépassement de capacité avec grandes valeurs intégrales négatifs, **LONG_MIN** est retourné. **atoi** et **_wtoi** retourner **INT_MAX** et **INT_MIN** sur ces conditions. Dans tous les cas d’out-of-range, **errno** a la valeur **ERANGE**. Si le paramètre passé est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL** et retourne 0.

## <a name="remarks"></a>Notes

Ces fonctions convertissent une chaîne de caractères en une valeur entière (**atoi** et **_wtoi**). La chaîne d’entrée est une séquence de caractères qui peut être interprétée comme une valeur numérique du type spécifié. La fonction arrête de lire la chaîne d’entrée au premier caractère qu’elle ne peut pas reconnaître comme faisant partie d’un nombre. Ce caractère peut être le caractère Null ('\0' ou L'\0') terminant la chaîne.

Le *str* argument **atoi** et **_wtoi** a la forme suivante :

> [*espace blanc*] [*signe*] [*chiffres*]]

A *espace blanc* se compose de caractères espace ou tabulation, qui sont ignorés ; *signe* est plus (+) ou moins (-) ; et *chiffres* sont un ou plusieurs chiffres.

Les versions de ces fonctions avec le **_l** suffixe sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux actuels. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstoi**|**atoi**|**atoi**|**_wtoi**|
|**_ttoi**|**atoi**|**atoi**|**_wtoi**|

## <a name="requirements"></a>Spécifications

|Routines|En-tête requis|
|--------------|---------------------|
|**atoi**|\<stdlib.h>|
|**_atoi_l**, **_wtoi**, **_wtoi_l**|\<stdlib.h> ou \<wchar.h>|

## <a name="example"></a>Exemple

Ce programme montre comment les nombres stockés sous forme de chaînes peuvent être converties en valeurs numériques à l’aide de la **atoi** fonctions.

```C
// crt_atoi.c
// This program shows how numbers
// stored as strings can be converted to
// numeric values using the atoi functions.

#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
    char    *str = NULL;
    int     value = 0;

    // An example of the atoi function.
    str = "  -2309 ";
    value = atoi( str );
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );

    // Another example of the atoi function.
    str = "31412764";
    value = atoi( str );
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );

    // Another example of the atoi function
    // with an overflow condition occuring.
    str = "3336402735171707160320";
    value = atoi( str );
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: atoi( "  -2309 " ) = -2309
Function: atoi( "31412764" ) = 31412764
Function: atoi( "3336402735171707160320" ) = 2147483647
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
