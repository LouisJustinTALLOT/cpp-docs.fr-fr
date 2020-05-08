---
title: puts, _putws
ms.date: 4/2/2020
api_name:
- _putws
- puts
- _o__putws
- _o_puts
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _putts
- _putws
- puts
helpviewer_keywords:
- strings [C++], writing
- _putts function
- standard output, writing to
- putws function
- puts function
- putts function
- _putws function
ms.assetid: 32dada12-ed45-40ac-be06-3feeced9ecd6
ms.openlocfilehash: 2e581237c7b839af87df7bc88369f21751b855d2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916112"
---
# <a name="puts-_putws"></a>puts, _putws

Écrit une chaîne dans **stdout**.

## <a name="syntax"></a>Syntaxe

```C
int puts(
   const char *str
);
int _putws(
   const wchar_t *str
);
```

### <a name="parameters"></a>Paramètres

*Str*<br/>
Chaîne de sortie.

## <a name="return-value"></a>Valeur de retour

Retourne une valeur non négative si l’opération aboutit. Si **put** échoue, elle retourne **EOF**; Si **_putws** échoue, elle retourne **WEOF**. Si *Str* est un pointeur null, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions définissent **errno** sur **EINVAL** et retournent **EOF** ou **WEOF**.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes 

La fonction **put** écrit *Str* dans le flux de sortie standard **stdout**, en remplaçant le caractère null de fin de la chaîne (' \ 0 ') par un caractère de saut de ligne (' \n') dans le flux de sortie.

**_putws** est la version à caractères larges de **puts**; les deux fonctions se comportent de la même manière si le flux est ouvert en mode ANSI. **put** ne prend pas actuellement en charge la sortie dans un flux Unicode.

**_putwch** écrit des caractères Unicode en utilisant les paramètres régionaux actuels de la console.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_putts**|**puts**|**puts**|**_putws**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**puts**|\<stdio.h>|
|**_putws**|\<stdio.h>|

La console n’est pas prise en charge dans les applications de plateforme Windows universelle (UWP). Les handles de flux standard associés à la console, **stdin**, **stdout**et **stderr**, doivent être redirigés pour que les fonctions runtime C puissent les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a> Exemple

```C
// crt_puts.c
// This program uses puts to write a string to stdout.

#include <stdio.h>

int main( void )
{
   puts( "Hello world from puts!" );
}
```

### <a name="output"></a>Output

```Output
Hello world from puts!
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[fgets, fgetws](fgets-fgetws.md)<br/>
