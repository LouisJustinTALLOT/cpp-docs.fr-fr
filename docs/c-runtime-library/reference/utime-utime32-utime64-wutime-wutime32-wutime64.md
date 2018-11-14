---
title: _utime, _utime32, _utime64, _wutime, _wutime32, _wutime64
ms.date: 11/04/2016
apiname:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
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
- _tutime
- _utime64
- wutime
- utime32
- wutime64
- _utime
- wutime32
- _wutime
- utime
- utime64
- _wutime64
- _utime32
- _tutime64
- _wutime32
helpviewer_keywords:
- tutime function
- utime32 function
- utime64 function
- _utime function
- _tutime32 function
- time [C++], file modification
- wutime function
- _wutime function
- _wutime32 function
- _tutime64 function
- _tutime function
- files [C++], modification time
- _wutime64 function
- _utime32 function
- utime function
- _utime64 function
- wutime64 function
- wutime32 function
- tutime64 function
- tutime32 function
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
ms.openlocfilehash: 8e52845a828e272ff3b8458b299c3757b8def748
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524629"
---
# <a name="utime-utime32-utime64-wutime-wutime32-wutime64"></a>_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64

Définissent l’heure de modification des fichiers.

## <a name="syntax"></a>Syntaxe

```C
int _utime(
   const char *filename,
   struct _utimbuf *times
);
int _utime32(
   const char *filename,
   struct __utimbuf32 *times
);
int _utime64(
   const char *filename,
   struct __utimbuf64 *times
);
int _wutime(
   const wchar_t *filename,
   struct _utimbuf *times
);
int _wutime32(
   const wchar_t *filename,
   struct __utimbuf32 *times
);
int _wutime64(
   const wchar_t *filename,
   struct __utimbuf64 *times
);
```

### <a name="parameters"></a>Paramètres

*filename*<br/>
Pointeur désignant une chaîne qui contient le chemin ou le nom de fichier.

*heures*<br/>
Pointeur désignant les valeurs d’heure stockées.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne 0 si l’heure de modification de fichier a changé. Une valeur de retour de -1 indique une erreur. Si un paramètre non valide est transmis, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent -1 et **errno** est défini sur l’une des valeurs suivantes :

|Valeur de la variable errno|Condition|
|-|-|
| **EACCES** | Le chemin indique le répertoire ou un fichier en lecture seule. |
| **EINVAL** | Non valide *fois* argument |
| **EMFILE** | Trop de fichiers ouverts (le fichier doit être ouvert pour modifier son heure de modification). |
| **ENOENT** | Chemin ou nom de fichier introuvable. |

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

La date d’un fichier peut être modifiée si la date de modification est postérieure au 1er janvier 1970 à minuit et antérieure à la date de fin de la fonction utilisée. **_utime** et **_wutime** utiliser une valeur d’heure 64 bits, par conséquent, la date de fin est 23:59:59 le 31 décembre 3000, UTC. Si **_USE_32BIT_TIME_T** est définie pour forcer l’ancien comportement, la date de fin est 23:59:59 le 18 janvier 2038, UTC. **_utime32** ou **_wutime32** utiliser un type d’heure 32 bits ait ou non **_USE_32BIT_TIME_T** est défini, et ont toujours la date de fin antérieure. **_utime64** ou **_wutime64** toujours utiliser le type de temps 64 bits, donc ces fonctions prennent toujours en charge la date de fin ultérieure.

## <a name="remarks"></a>Notes

Le **_utime** fonction définit l’heure de modification pour le fichier spécifié par *filename*. Pour que la modification de l’heure soit possible, le processus doit avoir un accès en écriture au fichier. Dans le système d’exploitation Windows, vous pouvez modifier l’heure d’accès et l’heure de modification dans le **_utimbuf** structure. Si *fois* est un **NULL** pointeur, l’heure de modification est défini sur l’heure locale actuelle. Sinon, *fois* doit pointer vers une structure de type **_utimbuf**, définie dans SYS\UTIME. H.

Le **_utimbuf** structure stocke les heures d’accès et modification de fichier utilisés par **_utime** pour modifier les dates de modification de fichier. La structure a les champs suivants, qui sont tous deux de type **time_t**:

| Champ |   |
|-------|---|
| **actime** | Heure d’accès au fichier. |
| **modtime** | Heure de modification du fichier. |

Des versions spécifiques de la **_utimbuf** structure (**_utimebuf32** et **__utimbuf64**) sont définis en utilisant les versions 32 bits et 64 bits du type de temps. Elles sont utilisées dans les versions spécifiques 32 bits et 64 bits de cette fonction. **_utimbuf** lui-même par défaut utilise un type d’heure 64 bits, sauf si **_USE_32BIT_TIME_T** est défini.

**_utime** est identique à **_futime** , à ceci près que le *filename* argument de **_utime** est un nom de fichier ou un chemin d’accès à un fichier, plutôt qu’un descripteur de fichier d’un Ouvrez le fichier.

**_wutime** est une version à caractères larges de **_utime**; le *filename* l’argument de **_wutime** est une chaîne de caractères larges. Ces fonctions se comportent sinon de façon identique.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tutime**|**_utime**|**_utime**|**_wutime**|
|**_tutime32**|**_utime32**|**_utime32**|**_wutime32**|
|**_tutime64**|**_utime64**|**_utime64**|**_wutime64**|

## <a name="requirements"></a>Configuration requise

|Routine|En-têtes obligatoires|En-têtes facultatifs|
|-------------|----------------------|----------------------|
|**_utime**, **_utime32**, **_utime64**|\<sys/utime.h>|\<errno.h>|
|**_utime64**|\<sys/utime.h>|\<errno.h>|
|**_wutime**|\<utime.h> ou \<wchar.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Ce programme utilise **_utime** pour définir l’heure de modification de fichier à l’heure actuelle.

```C
// crt_utime.c
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/utime.h>
#include <time.h>

int main( void )
{
   struct tm tma = {0}, tmm = {0};
   struct _utimbuf ut;

   // Fill out the accessed time structure
   tma.tm_hour = 12;
   tma.tm_isdst = 0;
   tma.tm_mday = 15;
   tma.tm_min = 0;
   tma.tm_mon = 0;
   tma.tm_sec = 0;
   tma.tm_year = 103;

   // Fill out the modified time structure
   tmm.tm_hour = 12;
   tmm.tm_isdst = 0;
   tmm.tm_mday = 15;
   tmm.tm_min = 0;
   tmm.tm_mon = 0;
   tmm.tm_sec = 0;
   tmm.tm_year = 102;

   // Convert tm to time_t
   ut.actime = mktime(&tma);
   ut.modtime = mktime(&tmm);

   // Show file time before and after
   system( "dir crt_utime.c" );
   if( _utime( "crt_utime.c", &ut ) == -1 )
      perror( "_utime failed\n" );
   else
      printf( "File time modified\n" );
   system( "dir crt_utime.c" );
}
```

### <a name="sample-output"></a>Résultat de l'exemple

```Output
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/09/2003  05:38 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
File time modified
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/15/2002  12:00 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
```

## <a name="see-also"></a>Voir aussi

[Gestion du temps](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[_futime, _futime32, _futime64](futime-futime32-futime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[_stat, _wstat, fonctions](stat-functions.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
