---
title: putc, putwc
ms.date: 11/04/2016
api_name:
- putwc
- putc
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _puttc
- putwc
- putc
helpviewer_keywords:
- streams, writing characters to
- characters, writing
- putwc function
- putc function
- _puttc function
- puttc function
ms.assetid: a37b2e82-9d88-4565-8190-ff8d04c0ddb9
ms.openlocfilehash: 2fcd0ea2263cd858b0b4ce855f96c0389956ccc3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950094"
---
# <a name="putc-putwc"></a>putc, putwc

Écrit un caractère dans un flux.

## <a name="syntax"></a>Syntaxe

```C
int putc(
   int c,
   FILE *stream
);
wint_t putwc(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Caractère à écrire.

*stream*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

Retourne le caractère écrit. Pour indiquer une erreur ou une condition de fin de fichier, **putc** et **putchar** retournent **EOF**; **putwc** et **putwchar** retournent **WEOF**. Pour les quatre routines, utilisez [ferror](ferror.md) ou [feof](feof.md) pour rechercher la présence d’une erreur ou d’une fin de fichier. Si un pointeur null est passé pour *Stream*, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **EOF** ou **WEOF** et attribuent à **errno** la valeur **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La routine **putc** écrit le caractère unique *c* dans le *flux* de sortie à la position actuelle. Tout entier peut être passé à **putc**, mais seuls les 8 bits de poids faible sont écrits. La routine **putchar** est identique à `putc( c, stdout )`. Pour chaque routine, si une erreur de lecture se produit, l’indicateur d’erreur du flux est défini. **putc** et **putchar** sont similaires à **fputc** et **_fputchar**, respectivement, mais sont implémentés en tant que fonctions et en tant que macros (consultez [choix entre les fonctions et les macros](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** et **putwchar** sont respectivement des versions à caractères larges de **putc** et **putchar**. **putwc** et **putc** se comportent de la même manière si le flux est ouvert en mode ANSI. **putc** ne prend pas actuellement en charge la sortie dans un flux Unicode.

Les versions avec suffixe **_nolock** sont identiques, à ceci près qu’elles ne sont pas protégées contre les interférences avec d’autres threads. Pour plus d’informations, consultez **_putc_nolock, _putwc_nolock**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttc**|**putc**|**putc**|**putwc**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**putc**|\<stdio.h>|
|**putwc**|\<stdio.h> ou \<wchar.h>|

La console n’est pas prise en charge dans les applications de plateforme Windows universelle (UWP). Les handles de flux standard associés à la console, **stdin**, **stdout**et **stderr**, doivent être redirigés pour que les fonctions runtime C puissent les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_putc.c
/* This program uses putc to write buffer
* to a stream. If an error occurs, the program
* stops before writing the entire buffer.
*/

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char *p, buffer[] = "This is the line of output\n";
   int  ch;

   ch = 0;
   /* Make standard out the stream and write to it. */
   stream = stdout;
   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = putc( *p, stream );
}
```

### <a name="output"></a>Sortie

```Output
This is the line of output
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
