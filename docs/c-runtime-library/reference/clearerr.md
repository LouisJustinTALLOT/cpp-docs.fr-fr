---
title: clearerr
ms.date: 11/04/2016
api_name:
- clearerr
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
- clearerr
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
ms.openlocfilehash: 9fd2f7e7dfcf272e806a887b356418b7555913f5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942947"
---
# <a name="clearerr"></a>clearerr

Réinitialiser l’indicateur d’erreur pour un flux. Une version plus sécurisée de cette fonction est disponible. Consultez [clearerr_s](clearerr-s.md).

## <a name="syntax"></a>Syntaxe

```C
void clearerr(
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*stream*<br/>
Pointeur désignant la structure **FILE**.

## <a name="remarks"></a>Notes

La fonction **clearerr** réinitialise l’indicateur d’erreur et l’indicateur de fin de fichier pour *Stream*. Les indicateurs d’erreur ne sont pas automatiquement effacés. une fois que l’indicateur d’erreur pour un flux spécifié est défini, les opérations sur ce flux continuent de retourner une valeur d’erreur jusqu’à ce que **clearerr**, [fseek](fseek-fseeki64.md), **fsetpos**ou [Rewind](rewind.md) soit appelé.

Si *Stream* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne. Pour plus d’informations sur la fonction **errno** et les codes d’erreur, consultez [errno, constantes](../../c-runtime-library/errno-constants.md).

Une version plus sécurisée de cette fonction est disponible. Consultez [clearerr_s](clearerr-s.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**clearerr**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_clearerr.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      clearerr( stdin );
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      clearerr( stdin );
   }
   else
      printf( "No read error\n" );
}
```

### <a name="input"></a>Entrée

```Input
n
```

### <a name="output"></a>Sortie

```Output
Write error: No error
Will input cause an error? n
No read error
```

## <a name="see-also"></a>Voir aussi

[Gestion des erreurs](../../c-runtime-library/error-handling-crt.md)<br/>
[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
