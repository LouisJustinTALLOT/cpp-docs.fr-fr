---
title: putchar, putwchar
ms.date: 4/2/2020
api_name:
- putchar
- putwchar
- _o_putchar
- _o_putwchar
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 09ad53a7f4e953da05d7eafd6662bf250731b5d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333127"
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

*C*<br/>
Caractère à écrire.

## <a name="return-value"></a>Valeur de retour

Retourne le caractère écrit. Pour indiquer une erreur ou une condition de fin de dossier, **putc** et **putchar** retournent **EOF**; **putwc** et **putwchar** retour **WEOF**. Pour les quatre routines, utilisez [ferror](ferror.md) ou [feof](feof.md) pour rechercher la présence d’une erreur ou d’une fin de fichier. Si passé un pointeur nul pour *le flux*, ces fonctions génèrent une exception de paramètre invalide, comme décrit dans La validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ils retournent **EOF** ou **WEOF** et mettent **errno** à **EINVAL**.

Consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces éléments et autres codes d’erreur.

## <a name="remarks"></a>Notes

La routine **putc** écrit le caractère *unique c* au *flux* de sortie à la position actuelle. N’importe quel intégrant peut être passé au **putc,** mais seulement les 8 bits inférieurs sont écrits. La routine **putchar** `putc( c, stdout )`est identique à . Pour chaque routine, si une erreur de lecture se produit, l’indicateur d’erreur du flux est défini. **putc** et **putchar** sont similaires à **fputc** et **_fputchar**, respectivement, mais sont mis en œuvre à la fois comme fonctions et comme macros (voir [Choisir entre les fonctions et les macros](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** et **putwchar** sont des versions à caractère large de **putc** et **putchar**, respectivement.

Les versions avec suffixe **_nolock** sont identiques, à ceci près qu’elles ne sont pas protégées contre les interférences avec d’autres threads. Elles peuvent être plus rapides, car elles n’entraînent pas la surcharge liée au verrouillage des autres threads. Utilisez ces fonctions uniquement dans les contextes thread-safe, tels que les applications à un seul thread ou lorsque la portée appelante gère déjà l'isolation des threads.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttchar**|**putchar**|**putchar**|**putwchar**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**putchar**|\<stdio.h>|
|**putwchar**|\<stdio.h> ou \<wchar.h>|

La console n’est pas prise en charge dans les applications Universal Windows Platform (UWP). Les poignées de flux standard qui sont associées à la console, **stdin**, **stdout**, et **stderr**, doivent être redirigés avant que les fonctions C run-time peuvent les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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

### <a name="output"></a>Output

```Output
This is the line of output
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
