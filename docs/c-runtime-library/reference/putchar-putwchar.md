---
description: 'En savoir plus sur : putchar, putwchar'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 5e4f374509b17d0a075944e333e73139dd69ea99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97270990"
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

## <a name="return-value"></a>Valeur renvoyée

Retourne le caractère écrit. Pour indiquer une erreur ou une condition de fin de fichier, **putc** et **putchar** retournent **EOF**; **putwc** et **putwchar** retournent **WEOF**. Pour les quatre routines, utilisez [ferror](ferror.md) ou [feof](feof.md) pour rechercher la présence d’une erreur ou d’une fin de fichier. Si un pointeur null est passé pour *Stream*, ces fonctions génèrent une exception de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, elles retournent **EOF** ou **WEOF** et attribuent à **errno** la valeur **EINVAL**.

Consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces éléments et autres codes d’erreur.

## <a name="remarks"></a>Notes

La routine **putc** écrit le caractère unique *c* dans le *flux* de sortie à la position actuelle. Tout entier peut être passé à **putc**, mais seuls les 8 bits de poids faible sont écrits. La routine **putchar** est identique à `putc( c, stdout )` . Pour chaque routine, si une erreur de lecture se produit, l’indicateur d’erreur du flux est défini. **putc** et **putchar** sont similaires à **fputc** et **_fputchar**, respectivement, mais sont implémentés en tant que fonctions et en tant que macros (consultez [choix entre les fonctions et les macros](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)). **putwc** et **putwchar** sont respectivement des versions à caractères larges de **putc** et **putchar**.

Les versions avec suffixe **_nolock** sont identiques, à ceci près qu’elles ne sont pas protégées contre les interférences avec d’autres threads. Elles peuvent être plus rapides, car elles n’entraînent pas la surcharge liée au verrouillage des autres threads. Utilisez ces fonctions uniquement dans les contextes thread-safe, tels que les applications à un seul thread ou lorsque la portée appelante gère déjà l'isolation des threads.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_puttchar**|**putchar**|**putchar**|**putwchar**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**putchar**|\<stdio.h>|
|**putwchar**|\<stdio.h> ou \<wchar.h>|

La console n’est pas prise en charge dans les applications de plateforme Windows universelle (UWP). Les handles de flux standard associés à la console, **stdin**, **stdout** et **stderr**, doivent être redirigés pour que les fonctions runtime C puissent les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
