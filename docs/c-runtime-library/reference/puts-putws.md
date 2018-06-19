---
title: puts, _putws | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _putws
- puts
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _putts
- _putws
- puts
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], writing
- _putts function
- standard output, writing to
- putws function
- puts function
- putts function
- _putws function
ms.assetid: 32dada12-ed45-40ac-be06-3feeced9ecd6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8a0b4f0c4924970905cb541d82450a807de1357
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404527"
---
# <a name="puts-putws"></a>puts, _putws

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

*str*<br/>
Chaîne de sortie.

## <a name="return-value"></a>Valeur de retour

Retourne une valeur non négative si l’opération aboutit. Si **place** échoue, elle retourne **EOF**; si **_putws** échoue, elle retourne **WEOF**. Si *str* est un pointeur null, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, les fonctions définissent **errno** à **EINVAL** et retourner **EOF** ou **WEOF**.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **place** fonction écritures *str* au flux de sortie standard **stdout**, en remplaçant la chaîne de terminer le caractère null ('\0') avec un caractère de saut de ligne ('\n') dans le flux de sortie.

**_putws** est la version à caractères larges de **place**; les deux fonctions se comportent de façon identique si le flux est ouvert en mode ANSI. **place** ne prend actuellement en charge la sortie dans un flux de données UNICODE.

**_putwch** écrit des caractères Unicode à l’aide de la valeur actuelle de la CONSOLE LOCALE.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_putts**|**puts**|**puts**|**_putws**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**puts**|\<stdio.h>|
|**_putws**|\<stdio.h>|

La console n’est pas pris en charge dans les applications de plateforme Windows universelle (UWP). Les descripteurs de flux standard qui sont associés à la console, **stdin**, **stdout**, et **stderr**, doivent être redirigés avant que les fonctions d’exécution C de les utiliser dans les applications UWP . Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_puts.c
// This program uses puts to write a string to stdout.

#include <stdio.h>

int main( void )
{
   puts( "Hello world from puts!" );
}
```

### <a name="output"></a>Sortie

```Output
Hello world from puts!
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[fgets, fgetws](fgets-fgetws.md)<br/>
