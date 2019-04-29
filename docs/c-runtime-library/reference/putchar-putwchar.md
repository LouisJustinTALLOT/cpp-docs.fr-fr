---
title: putchar, putwchar
ms.date: 11/04/2016
apiname:
- putchar
- putwchar
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
- putchar
- putwchar
- _puttchar
helpviewer_keywords:
- putchar function
- _puttchar function
- characters, writing
- standard output, writing to
- putwchar function
ms.assetid: 93657c7f-cca1-4032-8e3a-cd6ab6193748
ms.openlocfilehash: becee3d79f58ac018d1161c1af36e9a4646640bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357986"
---
# <a name="putchar-putwchar"></a>putchar, putwchar

Écrit un caractère dans **stdout**.

## <a name="syntax"></a>Syntaxe

```C
int putchar(
   int c
);
wint_t putwchar(
   wchar_t c
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Caractère à écrire.

## <a name="return-value"></a>Valeur de retour

Retourne le caractère écrit. Pour indiquer une erreur ou une condition de fin de fichier, **putc** et **putchar** retourner **EOF**; **putwc** et **putwchar** retourner **WEOF**. Pour les quatre routines, utilisez [ferror](ferror.md) ou [feof](feof.md) pour rechercher la présence d’une erreur ou d’une fin de fichier. Si passé un pointeur null pour *flux*, ces fonctions génèrent une exception de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, elles retournent **EOF** ou **WEOF** et définissez **errno** à **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **putc** routine écrit le caractère unique *c* à la sortie *flux* à la position actuelle. N’importe quel entier peut être passé à **putc**, mais uniquement les 8 derniers bits sont écrits. Le **putchar** routine est identique à `putc( c, stdout )`. Pour chaque routine, si une erreur de lecture se produit, l’indicateur d’erreur du flux est défini. **putc** et **putchar** sont similaires aux **fputc** et **_fputchar**, respectivement, mais sont implémentées en tant que fonctions et en tant que macros (consultez [ Choix entre fonctions et Macros](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** et **putwchar** sont des versions à caractères larges de **putc** et **putchar**, respectivement.

Les versions avec suffixe **_nolock** sont identiques, à ceci près qu’elles ne sont pas protégées contre les interférences avec d’autres threads. Elles peuvent être plus rapides, car elles n’entraînent pas la surcharge liée au verrouillage des autres threads. Utilisez ces fonctions uniquement dans les contextes thread-safe, tels que les applications à un seul thread ou lorsque la portée appelante gère déjà l'isolation des threads.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttchar**|**putchar**|**putchar**|**putwchar**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**putchar**|\<stdio.h>|
|**putwchar**|\<stdio.h> ou \<wchar.h>|

La console n’est pas pris en charge dans les applications Universal Windows Platform (UWP). Les handles de flux standard qui sont associés à la console, **stdin**, **stdout**, et **stderr**, doivent être redirigés pour que les fonctions runtime C de les utiliser dans les applications UWP . Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_putchar.c
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

   for( p = buffer; (ch != EOF) && (*p != '\0'); p++ )
      ch = putchar( *p );
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
