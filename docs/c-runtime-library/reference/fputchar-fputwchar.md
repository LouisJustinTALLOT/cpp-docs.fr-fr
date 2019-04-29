---
title: _fputchar, _fputwchar
ms.date: 11/04/2016
apiname:
- _fputchar
- _fputwchar
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
- fputtchar
- _fputwchar
- fputwchar
- _fputtchar
- fputchar
- _fputchar
helpviewer_keywords:
- fputchar function
- standard output, writing to
- _fputtchar function
- fputwchar function
- _fputwchar function
- fputtchar function
- _fputchar function
ms.assetid: b92ff600-a924-4f2b-b0e7-3097ee31bdff
ms.openlocfilehash: 57ec2350fa1d0b681c6eed0c4cfc4ec4660977e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287928"
---
# <a name="fputchar-fputwchar"></a>_fputchar, _fputwchar

Écrit un caractère dans **stdout**.

## <a name="syntax"></a>Syntaxe

```C
int _fputchar(
   int c
);
wint_t _fputwchar(
   wchar_t c
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Caractère à écrire.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne le caractère écrit. Pour **_fputchar**, une valeur de retour de **EOF** indique une erreur. Pour **_fputwchar**, une valeur de retour de **WEOF** indique une erreur. Si c est **NULL**, ces fonctions génèrent une exception de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, elles retournent **EOF** (ou **WEOF**) et définissez **errno** à **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Ces deux fonctions écrit le caractère unique *c* à **stdout** et avance l’indicateur comme il convient. **_fputchar** équivaut à `fputc( stdout )`. Il est également équivalent à **putchar**, mais implémentée uniquement comme une fonction, plutôt que comme une fonction et une macro. Contrairement aux **fputc** et **putchar**, ces fonctions ne sont pas compatibles avec la norme ANSI.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fputtchar**|**_fputchar**|**_fputchar**|**_fputwchar**|

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fputchar**|\<stdio.h>|
|**_fputwchar**|\<stdio.h> ou \<wchar.h>|

La console n’est pas pris en charge dans les applications Universal Windows Platform (UWP). Les handles de flux standard qui sont associés à la console,**stdin**, **stdout**, et **stderr**— doivent être redirigés pour que les fonctions runtime C de les utiliser dans les applications UWP . Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_fputchar.c
// This program uses _fputchar
// to send a character array to stdout.

#include <stdio.h>

int main( void )
{
    char strptr[] = "This is a test of _fputchar!!\n";
    char *p = NULL;

    // Print line to stream using _fputchar.
    p = strptr;
    while( (*p != '\0') && _fputchar( *(p++) ) != EOF )
      ;
}
```

```Output
This is a test of _fputchar!!
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
