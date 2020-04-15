---
title: setvbuf
ms.date: 4/2/2020
api_name:
- setvbuf
- _o_setvbuf
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
- setvbuf
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
ms.openlocfilehash: 203265a8dd85854bcedd737359b856fdc4cce04d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316267"
---
# <a name="setvbuf"></a>setvbuf

Contrôle la mise en mémoire tampon du flux et la taille de la mémoire tampon.

## <a name="syntax"></a>Syntaxe

```C
int setvbuf(
   FILE *stream,
   char *buffer,
   int mode,
   size_t size
);
```

### <a name="parameters"></a>Paramètres

*Flux*<br/>
Pointeur désignant la structure **FILE**.

*buffer*<br/>
Mémoire tampon allouée par l’utilisateur.

*mode*<br/>
Mode de mise en mémoire tampon.

*Taille*<br/>
Taille de la mémoire tampon en octets. Gamme admissible : 2 <et *taille* <INT_MAX (2147483647). En interne, la valeur fournie pour la *taille* est arrondie vers le bas au multiple le plus proche de 2.

## <a name="return-value"></a>Valeur de retour

Retourne 0 en cas de réussite.

Si *le flux* est **NULL**, ou si *le mode* ou la *taille* n’est pas dans une modification valide, le gestionnaire de paramètres invalide est invoqué, tel que décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne -1 et définit **errno** sur **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **setvbuf** permet au programme de contrôler à la fois la mise en mémoire tampon et la taille du tampon pour *le flux*. *flux* doit se référer à un fichier ouvert qui n’a pas subi une opération I / O depuis son ouverture. Le tableau pointé par *le tampon* est utilisé comme tampon, sauf si c’est **NULL**, auquel \* cas **setvbuf** utilise un tampon automatiquement alloué de la *taille*de longueur /2 2 octets.

Le mode doit être **_IOFBF,** **_IOLBF,** ou **_IONBF**. Si *le mode* est **_IOFBF** ou **_IOLBF,** alors la *taille* est utilisée comme la taille du tampon. Si *le mode* est **_IONBF,** le flux est inbuffered et *la taille* et le *tampon* sont ignorés. Les valeurs pour *le mode* et leurs significations sont les :

|valeur *du mode*|Signification|
|-|-|
| **_IOFBF** | Tampon complet; *c’est-à-dire* que le tampon est utilisé comme tampon et la *taille* est utilisée comme la taille du tampon. Si *le tampon* est **NULL**, un octets de *taille* tampon automatiquement allouée long est utilisé. |
| **_IOLBF** | Pour certains systèmes, ce mode assure une mise en mémoire tampon de ligne. Cependant, pour Win32, le comportement est le même que **_IOFBF** - Full Buffering. |
| **_IONBF** | Aucun tampon n’est utilisé, indépendamment du *tampon* ou de la *taille.* |

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**setvbuf**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_setvbuf.c
// This program opens two streams: stream1
// and stream2. It then uses setvbuf to give stream1 a
// user-defined buffer of 1024 bytes and stream2 no buffer.
//

#include <stdio.h>

int main( void )
{
   char buf[1024];
   FILE *stream1, *stream2;

   if( fopen_s( &stream1, "data1", "a" ) == 0 &&
       fopen_s( &stream2, "data2", "w" ) == 0 )
   {
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )
         printf( "Incorrect type or size of buffer for stream1\n" );
      else
         printf( "'stream1' now has a buffer of 1024 bytes\n" );
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )
         printf( "Incorrect type or size of buffer for stream2\n" );
      else
         printf( "'stream2' now has no buffer\n" );
      _fcloseall();
   }
}
```

```Output
'stream1' now has a buffer of 1024 bytes
'stream2' now has no buffer
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setbuf](setbuf.md)<br/>
