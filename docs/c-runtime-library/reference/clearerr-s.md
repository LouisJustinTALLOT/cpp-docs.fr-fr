---
title: clearerr_s
ms.date: 11/04/2016
api_name:
- clearerr_s
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
- clearerr_s
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr_s function
ms.assetid: b74d014d-b7a8-494a-a330-e5ffd5614772
ms.openlocfilehash: 12e76ba5133d99ed2d45d7cf15bada2ad1c5c38b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939153"
---
# <a name="clearerr_s"></a>clearerr_s

Réinitialiser l’indicateur d’erreur pour un flux. Il s’agit d’une version de [clearerr](clearerr.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t clearerr_s(
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*stream*<br/>
Pointeur vers la structure de **fichier**

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite ; **EINVAL** si *Stream* a la **valeur null**.

## <a name="remarks"></a>Notes

La fonction **clearerr_s** réinitialise l’indicateur d’erreur et l’indicateur de fin de fichier pour *Stream*. Les indicateurs d’erreur ne sont pas automatiquement effacés. une fois que l’indicateur d’erreur pour un flux spécifié est défini, les opérations sur ce flux continuent de retourner une valeur d’erreur jusqu’à ce que **clearerr_s**, **clearerr**, [fseek](fseek-fseeki64.md), **fsetpos**ou [Rewind](rewind.md) soit appelé.

Si *Stream* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne **EINVAL**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**clearerr_s**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

```C
// crt_clearerr_s.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   errno_t err;

   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }
}
```

### <a name="input"></a>Entrée

```Input
n
```

### <a name="output"></a>Sortie

```Output
Write error: Bad file descriptor
Will input cause an error? n
```

## <a name="see-also"></a>Voir aussi

[Gestion des erreurs](../../c-runtime-library/error-handling-crt.md)<br/>
[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
