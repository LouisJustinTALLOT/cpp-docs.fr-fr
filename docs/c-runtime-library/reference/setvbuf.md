---
title: setvbuf | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- setvbuf
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
- setvbuf
dev_langs:
- C++
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c516932eb8d50fb8c9fdbe6f8c48a3f590b1ffb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408482"
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

*Flux de données*<br/>
Pointeur désignant la structure **FILE**.

*buffer*<br/>
Mémoire tampon allouée par l’utilisateur.

*mode*<br/>
Mode de mise en mémoire tampon.

*size*<br/>
Taille de la mémoire tampon en octets. Plage autorisée : 2 < = *taille* < = INT_MAX (2147483647). En interne, la valeur fournie pour *taille* est arrondie au multiple plus proche de 2.

## <a name="return-value"></a>Valeur de retour

Retourne 0 en cas de réussite.

Si *flux* est **NULL**, ou si *mode* ou *taille* est n’est pas dans une modification valide, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne -1 et affecte **errno** à **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **setvbuf** fonction permet au programme de contrôle à la fois mise en mémoire tampon et de la mémoire tampon de taille pour *flux*. *flux* doit faire référence à un fichier ouvert qui n’a pas subi une opération d’e/s, car il a été ouvert. Le tableau vers lequel pointe *tampon* est utilisé en tant que la mémoire tampon, sauf s’il est **NULL**, auquel cas **setvbuf** utilise un tampon alloué automatiquement de longueur  *taille*/2 * 2 octets.

Le mode doit être **_IOFBF**, **_IOLBF**, ou **_IONBF**. Si *mode* est **_IOFBF** ou **_IOLBF**, puis *taille* est utilisé en tant que la taille de la mémoire tampon. Si *mode* est **_IONBF**, le flux est tamponné et *taille* et *tampon* sont ignorés. Les valeurs pour *mode* et leurs significations sont :

|*mode* valeur|Signification|
|-|-|
**_IOFBF**|Mise en mémoire tampon complète ; Autrement dit, *tampon* est utilisé en tant que la mémoire tampon et *taille* est utilisé en tant que la taille de la mémoire tampon. Si *tampon* est **NULL**, une mémoire tampon allouée automatiquement *taille* octets de long est utilisé.
**_IOLBF**|Pour certains systèmes, ce mode assure une mise en mémoire tampon de ligne. Toutefois, pour Win32, le comportement est identique à **_IOFBF** -mise en mémoire tampon complète.
**_IONBF**|Aucune mémoire tampon n’est utilisé, quel que soit le *tampon* ou *taille*.

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
