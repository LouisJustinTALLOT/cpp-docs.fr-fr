---
title: _putw
ms.date: 4/2/2020
api_name:
- _putw
- _o__putw
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
- _putw
helpviewer_keywords:
- integers, writing to streams
- putw function
- streams, writing integers to
- _putw function
ms.assetid: 83d63644-249d-4a39-87e5-3b7aa313968d
ms.openlocfilehash: c54490a5625bfa2f9ffc95d616c2d73a7acf98e5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916081"
---
# <a name="_putw"></a>_putw

Écrit un entier dans un flux.

## <a name="syntax"></a>Syntaxe

```C
int _putw(
   int binint,
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*binint*<br/>
Entier binaire à sortir.

*train*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

Retourne la valeur écrite. Une valeur de retour de **EOF** peut indiquer une erreur. Comme **EOF** est également une valeur entière légitime **, utilisez l'** attaquant pour vérifier une erreur. Si *Stream* est un pointeur null, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne **EOF**.

Pour obtenir des informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes 

La fonction **_putw** écrit une valeur binaire de type **int** à la position actuelle du *flux.* **_putw** n’affecte pas l’alignement des éléments dans le flux et n’assume pas l’alignement spécial. **_putw** est principalement destiné à la compatibilité avec les bibliothèques précédentes. Des problèmes de portabilité peuvent survenir avec **_putw** car la taille d’un **int** et l’ordre des octets dans un **int** diffèrent entre les systèmes.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_putw**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a> Exemple

```C
// crt_putw.c
/* This program uses _putw to write a
* word to a stream, then performs an error check.
*/

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   unsigned u;
   if( fopen_s( &stream, "data.out", "wb" ) )
      exit( 1 );
   for( u = 0; u < 10; u++ )
   {
      _putw( u + 0x2132, stream );   /* Write word to stream. */
      if( ferror( stream ) )         /* Make error check. */
      {
         printf( "_putw failed" );
         clearerr_s( stream );
         exit( 1 );
      }
   }
   printf( "Wrote ten words\n" );
   fclose( stream );
}
```

### <a name="output"></a>Output

```Output
Wrote ten words
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_getw](getw.md)<br/>
