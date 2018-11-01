---
title: _futime, _futime32, _futime64
ms.date: 11/04/2016
apiname:
- _futime64
- _futime32
- _futime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- futime
- _futime
- futime64
- _futime64
helpviewer_keywords:
- _futime function
- futime32 function
- futime64 function
- file modification time [C++]
- _futime64 function
- futime function
- _futime32 function
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
ms.openlocfilehash: f21e394acdcc7fbf8a91c5450a4c04daa050db21
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652502"
---
# <a name="futime-futime32-futime64"></a>_futime, _futime32, _futime64

Définit l’heure de modification d’un fichier ouvert.

## <a name="syntax"></a>Syntaxe

```C
int _futime(
   int fd,
   struct _utimbuf *filetime
);
int _futime32(
   int fd,
   struct __utimbuf32 *filetime
);
int _futime64(
   int fd,
   struct __utimbuf64 *filetime
);
```

### <a name="parameters"></a>Paramètres

*fd*<br/>
Descripteur du fichier ouvert.

*FILETIME*<br/>
Pointeur désignant la structure qui contient la nouvelle date de modification.

## <a name="return-value"></a>Valeur de retour

Retournent 0 en cas de réussite. Si une erreur se produit, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne -1 et **errno** a la valeur **EBADF**, indiquant un descripteur de fichier non valide, ou **EINVAL**, indiquant un non valide paramètre.

## <a name="remarks"></a>Notes

Le **_futime** routine définit la date de modification et l’heure d’accès sur le fichier ouvert associé *fd*. **_futime** est identique à [_utime](utime-utime32-utime64-wutime-wutime32-wutime64.md), à ceci près que son argument est le descripteur de fichier d’un fichier ouvert, plutôt que le nom d’un fichier ou un chemin d’accès à un fichier. Le **_utimbuf** structure contient des champs pour la nouvelle date de modification et l’heure de l’accès. Les deux champs doivent contenir des valeurs valides. **_utimbuf32** et **_utimbuf64** sont identiques aux **_utimbuf** sauf pour l’utilisation des types de temps 32 bits et 64 bits, respectivement. **_futime** et **_utimbuf** utilisent un type d’heure de 64 bits et **_futime** est un comportement identique à **_futime64**. Si vous avez besoin forcer l’ancien comportement, définissez **_USE_32BIT_TIME_T**. Cela alors **_futime** à être un comportement identique à **_futime32** et provoque la **_utimbuf** structure à utiliser le type au moment de 32 bits, ce qui équivaut à **__utimbuf32**.

**_futime64**, qui utilise le **__utimbuf64** structure peuvent lire et modifier les dates de fichier à 23:59:59 le 31 décembre 3000, UTC ; alors qu’un appel à **_futime32** échoue si la date sur le fichier est ultérieure à 23:59:59 le 18 janvier 2038, UTC. Le 1er janvier 1970 à minuit est la limite inférieure de la plage de dates pour ces fonctions.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|En-tête facultatif|
|--------------|---------------------|---------------------|
|**_futime**|\<sys/utime.h>|\<errno.h>|
|**_futime32**|\<sys/utime.h>|\<errno.h>|
|**_futime64**|\<sys/utime.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_futime.c
// This program uses _futime to set the
// file-modification time to the current time.

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <io.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <sys/utime.h>
#include <share.h>

int main( void )
{
   int hFile;

   // Show file time before and after.
   system( "dir crt_futime.c_input" );

   _sopen_s( &hFile, "crt_futime.c_input", _O_RDWR, _SH_DENYNO, 0 );

   if( _futime( hFile, NULL ) == -1 )
      perror( "_futime failed\n" );
   else
      printf( "File time modified\n" );

   _close (hFile);

   system( "dir crt_futime.c_input" );
}
```

### <a name="input-crtfutimecinput"></a>Entrée : crt_futime.c_input

```Input
Arbitrary file contents.
```

### <a name="sample-output"></a>Résultat de l'exemple

```Output
Volume in drive Z has no label.
Volume Serial Number is 5C68-57C1

Directory of Z:\crt

03/25/2004  10:40 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
Volume in drive Z has no label.
Volume Serial Number is 5C68-57C1

Directory of Z:\crt

03/25/2004  10:41 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
File time modified
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
