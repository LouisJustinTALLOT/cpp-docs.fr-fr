---
title: clearerr
ms.date: 11/04/2016
apiname:
- clearerr
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
- clearerr
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr function
ms.assetid: a9711cd4-3335-43d4-a018-87bbac5b3bac
ms.openlocfilehash: 2e2bf43946f8f306ce120cb48998b84c5ae09bf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646327"
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

*flux de données*<br/>
Pointeur désignant la structure **FILE**.

## <a name="remarks"></a>Notes

Le **clearerr** fonction réinitialise l’indicateur d’erreur et l’indicateur de fin de fichier pour *flux*. Indicateurs d’erreur ne sont pas effacés automatiquement ; une fois que l’indicateur d’erreur pour un flux de données spécifié est défini, les opérations sur ce flux continuent de retourner une valeur d’erreur jusqu'à ce que **clearerr**, [fseek](fseek-fseeki64.md), **fsetpos**, ou [rewind](rewind.md) est appelée.

Si *flux* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne. Pour plus d’informations sur **errno** et les codes d’erreur, consultez [constantes errno](../../c-runtime-library/errno-constants.md).

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

```Output

n

```

```Output

      nWrite error: No error
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
