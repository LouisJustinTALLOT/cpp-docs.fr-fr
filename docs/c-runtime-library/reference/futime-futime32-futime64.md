---
description: 'En savoir plus sur les éléments suivants : _futime, _futime32 _futime64'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: d0e438c14d8fa7ba472be77d9d6f064b41d61431
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273759"
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

*FD*<br/>
Descripteur du fichier ouvert.

*FILETIME*<br/>
Pointeur désignant la structure qui contient la nouvelle date de modification.

## <a name="return-value"></a>Valeur renvoyée

Retournent 0 en cas de réussite. Si une erreur se produit, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction retourne-1 et **errno** a la valeur **EBADF**, ce qui indique un descripteur de fichier non valide, ou **EINVAL**, qui indique un paramètre non valide.

## <a name="remarks"></a>Notes

La routine **_futime** définit la date de modification et l’heure d’accès du fichier ouvert associé à *FD*. **_futime** est identique à [_utime](utime-utime32-utime64-wutime-wutime32-wutime64.md), sauf que son argument est le descripteur de fichier d’un fichier ouvert, plutôt que le nom d’un fichier ou un chemin d’accès à un fichier. La structure **_utimbuf** contient des champs pour la nouvelle date de modification et l’heure d’accès. Les deux champs doivent contenir des valeurs valides. les **_utimbuf32** et les **_utimbuf64** sont identiques à **_utimbuf** , à l’exception de l’utilisation des types d’heure 32 bits et 64 bits, respectivement. **_futime** et **_utimbuf** utilisent un type de temps de 64 bits et **_futime** sont identiques en ce qui concerne le comportement de **_futime64**. Si vous devez forcer l’ancien comportement, définissez **_USE_32BIT_TIME_T**. Dans ce cas, **_futime** est identique dans le comportement à **_futime32** et la structure **_utimbuf** utilise le type de temps 32 bits, ce qui en fait l’équivalent de **__utimbuf32**.

**_futime64**, qui utilise la structure **__utimbuf64** , peut lire et modifier les dates des fichiers jusqu' 23:59:59, 31 décembre 3000, UTC ; tandis qu’un appel à **_futime32** échoue si la date du fichier est ultérieure au 18 23:59:59 Janvier 2038, heure UTC. Le 1er janvier 1970 à minuit est la limite inférieure de la plage de dates pour ces fonctions.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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
