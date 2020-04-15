---
title: _futime, _futime32, _futime64
ms.date: 4/2/2020
api_name:
- _futime64
- _futime32
- _futime
- _o__futime32
- _o__futime64
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 1f60bb3b366c48e3d53368f81ebc2528694794f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345503"
---
# <a name="_futime-_futime32-_futime64"></a>_futime, _futime32, _futime64

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

*Fd*<br/>
Descripteur du fichier ouvert.

*temps de fichier*<br/>
Pointeur désignant la structure qui contient la nouvelle date de modification.

## <a name="return-value"></a>Valeur de retour

Retournent 0 en cas de réussite. Si une erreur se produit, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction renvoie -1 et **errno** est réglé sur **EBADF**, indiquant un descripteur de fichier invalide, ou **EINVAL**, indiquant un paramètre invalide.

## <a name="remarks"></a>Notes

La **routine _futime** fixe la date de modification et l’heure d’accès sur le fichier ouvert associé à *fd*. **_futime** est identique à [_utime,](utime-utime32-utime64-wutime-wutime32-wutime64.md)sauf que son argument est le descripteur de fichier d’un fichier ouvert, plutôt que le nom d’un fichier ou d’un chemin vers un fichier. La **structure _utimbuf** contient des champs pour la nouvelle date de modification et l’heure d’accès. Les deux champs doivent contenir des valeurs valides. **_utimbuf32** et **_utimbuf64** sont identiques à **_utimbuf,** sauf pour l’utilisation des types de temps 32 et 64 bits, respectivement. **_futime** et **_utimbuf** utiliser un type de temps 64 bits et **_futime** est identique dans le comportement à **_futime64**. Si vous avez besoin de forcer l’ancien comportement, définir **_USE_32BIT_TIME_T**. Cela provoque **_futime** d’être identique dans le comportement à **_futime32** et provoque la structure **_utimbuf** d’utiliser le type de temps 32 bits, ce qui le rend équivalent à **__utimbuf32**.

**_futime64**, qui utilise la structure **__utimbuf64,** peut lire et modifier les dates de fichier jusqu’à 23:59:59, Décembre 31, 3000, UTC; considérant qu’un appel à **_futime32** échoue si la date du dossier est postérieure à 23:59:59 Janvier 18, 2038, UTC. Le 1er janvier 1970 à minuit est la limite inférieure de la plage de dates pour ces fonctions.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|En-tête facultatif|
|--------------|---------------------|---------------------|
|**_futime**|\<sys/utime.h>|\<errno.h>|
|**_futime32**|\<sys/utime.h>|\<errno.h>|
|**_futime64**|\<sys/utime.h>|\<errno.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

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

### <a name="input-crt_futimec_input"></a>Entrée : crt_futime.c_input

```Input
Arbitrary file contents.
```

### <a name="sample-output"></a>Exemple de sortie

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
