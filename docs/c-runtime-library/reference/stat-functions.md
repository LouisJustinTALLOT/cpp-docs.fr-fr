---
title: _stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32
ms.date: 4/2/2020
api_name:
- _wstat64
- _stati64
- _stat32
- _stat32i64
- _stat
- _wstati64
- _wstat32
- _wstat64i32
- _wstat
- _stat64
- _stat64i32
- _wstat32i64
- _o__stat32
- _o__stat32i64
- _o__stat64
- _o__stat64i32
- _o__wstat32
- _o__wstat32i64
- _o__wstat64
- _o__wstat64i32
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tstat32
- tstat
- _tstat64i32
- tstati64
- _wstat64
- _wstat32
- wstati64
- tstat64
- _stati64
- _wstat
- wstat64i32
- stat32i64
- tstat32i64
- _tstat
- _wstati64
- _tstati64
- _wstat32i64
- wstat32
- _wstat64i32
- _stat
- _tstat32
- stat64i32
- wstat64
- stat
- _stat32i64
- _stat32
- stati64
- wstat
- _stat64i32
- stat32
- _tstat32i64
- tstat64i32
- _tstat64
- _stat64
- stat/_stat
- stat/_stat32
- stat/_stat64
- stat/_stati64
- stat/_stat32i64
- stat/_stat64i32
- stat/_wstat
- stat/_wstat32
- stat/_wstat64
- stat/_wstati64
- stat/_wstat32i64
- stat/_wstat64i32
helpviewer_keywords:
- files [C++], status information
- _stat function
- _wstat function
- _stat64i32 function
- tstat function
- _tstat64i32 function
- _stati64 function
- _stat64 function
- tstati64 function
- wstati64 function
- wstat64 function
- _wstat64i32 function
- _tstat32i64 function
- _stat32i64 function
- stat function
- status of files
- _tstat32 function
- tstat64 function
- _wstat64 function
- _tstat function
- _stat32 function
- wstat function
- _wstat32i64 function
- _tstati64 function
- _wstat32 function
- stat64 function
- stati64 function
- _wstati64 function
- _tstat64 function
- files [C++], getting status information
ms.assetid: 99a75ae6-ff26-47ad-af70-5ea7e17226a5
ms.openlocfilehash: 32a96a93eb8a18e366ac7a075b414dbca732fb61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355414"
---
# <a name="_stat-_stat32-_stat64-_stati64-_stat32i64-_stat64i32-_wstat-_wstat32-_wstat64-_wstati64-_wstat32i64-_wstat64i32"></a>_stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32

Obtenir des informations sur l’état d’un fichier.

## <a name="syntax"></a>Syntaxe

```C
int _stat(
   const char *path,
   struct _stat *buffer
);
int _stat32(
   const char *path,
   struct __stat32 *buffer
);
int _stat64(
   const char *path,
   struct __stat64 *buffer
);
int _stati64(
   const char *path,
   struct _stati64 *buffer
);
int _stat32i64(
   const char *path,
   struct _stat32i64 *buffer
);
int _stat64i32(
   const char *path,
   struct _stat64i32 *buffer
);
int _wstat(
   const wchar_t *path,
   struct _stat *buffer
);
int _wstat32(
   const wchar_t *path,
   struct __stat32 *buffer
);
int _wstat64(
   const wchar_t *path,
   struct __stat64 *buffer
);
int _wstati64(
   const wchar_t *path,
   struct _stati64 *buffer
);
int _wstat32i64(
   const wchar_t *path,
   struct _stat32i64 *buffer
);
int _wstat64i32(
   const wchar_t *path,
   struct _stat64i32 *buffer
);
```

### <a name="parameters"></a>Paramètres

*path*<br/>
Pointeur vers une chaîne contenant le chemin d’accès du fichier ou répertoire existant.

*buffer*<br/>
Pointeur vers une structure qui stocke les résultats.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne 0 si les informations sur l’état des fichiers sont obtenues. Une valeur de retour de -1 indique une erreur, auquel cas **errno** est réglé à **ENOENT**, indiquant que le nom de fichier ou le chemin n’a pas pu être trouvé. Une valeur de retour **d’EINVAL** indique un paramètre invalide; **errno** est également fixé à **EINVAL** dans ce cas.

Voir [_doserrno, errno, _sys_errlist, et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ce, et d’autres, codes de retour.

Le timbre de date d’un fichier peut être représenté s’il est plus tard que minuit, 1er janvier 1970, et avant 23:59:59, 31 décembre 3000, UTC, sauf si vous utilisez **_stat32** ou **_wstat32**, ou avez défini **_USE_32BIT_TIME_T**, auquel cas la date ne peut être représentée que jusqu’à 23:59:59 Janvier 18, 2038, UTC.

## <a name="remarks"></a>Notes

La fonction **_stat** obtient des informations sur le fichier ou l’annuaire spécifié par *chemin* et le stocke dans la structure pointée par *tampon*. **_stat** gère automatiquement les arguments de chaîne multioctets, le cas échéant, en reconnaissant les séquences multioctets-caractères selon la page de code multioctet actuellement en service.

**_wstat** est une version à caractère large de **_stat**; l’argument *de chemin* à **_wstat** est une chaîne de caractère large. **_wstat** et **_stat** se comportent de la même façon, sauf que **_wstat** ne gère pas les cordes multioctets.

Les variantes de ces fonctions prennent en charge les types d’heures 32 ou 64 bits et les longueurs de fichiers 32 ou 64 bits. Le premier suffixe numérique (**32** ou **64**) indique la taille du type de temps utilisé; le deuxième suffixe est **i32** ou **i64**, indiquant si la taille du fichier est représenté comme un intégriste 32 ou 64 bits.

**_stat** est équivalent à **_stat64i32,** et **la structure** **_stat** contient un temps de 64 bits. Cela est vrai à moins **que _USE_32BIT_TIME_T** ne soit définie, auquel cas l’ancien comportement est en vigueur; **_stat** utilise un temps de 32 bits, et **la structure** **_stat** contient un temps de 32 bits. Il en va de même pour **_stati64**.

> [!NOTE]
> **_wstat** ne fonctionne pas avec les liens symboliques windows Vista. Dans ces cas, **_wstat** signalera toujours une taille de fichier de 0. **_stat** fonctionne correctement avec des liens symboliques.

Cette fonction valide ses paramètres. Si le *chemin* ou le *tampon* est **NULL**, le gestionnaire de paramètre invalide est invoqué, tel que décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>Variantes de type d’heure et de type de longueur de fichier de _stat

|Fonctions|_USE_32BIT_TIME_T défini ?|Type d’heure|Type de longueur de fichier|
|---------------|------------------------------------|---------------|----------------------|
|**_stat**, **_wstat**|Non défini|64 bits|32 bits|
|**_stat**, **_wstat**|Défini|32 bits|32 bits|
|**_stat32**, **_wstat32**|Non affecté par la définition de macro|32 bits|32 bits|
|**_stat64**, **_wstat64**|Non affecté par la définition de macro|64 bits|64 bits|
|**_stati64**, **_wstati64**|Non défini|64 bits|64 bits|
|**_stati64**, **_wstati64**|Défini|32 bits|64 bits|
|**_stat32i64**, **_wstat32i64**|Non affecté par la définition de macro|32 bits|64 bits|
|**_stat64i32**, **_wstat64i32**|Non affecté par la définition de macro|64 bits|32 bits|

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstat**|**_stat**|**_stat**|**_wstat**|
|**_tstat64**|**_stat64**|**_stat64**|**_wstat64**|
|**_tstati64**|**_stati64**|**_stati64**|**_wstati64**|
|**_tstat32i64**|**_stat32i64**|**_stat32i64**|**_wstat32i64**|
|**_tstat64i32**|**_stat64i32**|**_stat64i32**|**_wstat64i32**|

La structure **_stat,** définie en SYS-STAT. H, comprend les champs suivants.

|Champ||
|-|-|
| **st_gid** | Identificateur numérique du groupe propriétaire du fichier (propre à UNIX). Ce champ est toujours zéro sur les systèmes Windows. Un fichier de redirection est classé comme un fichier Windows. |
| **st_atime** | Heure du dernier accès au fichier. Valide sur NTFS, mais pas sur les lecteurs de disque au format FAT. |
| **st_ctime** | Heure de création du fichier. Valide sur NTFS, mais pas sur les lecteurs de disque au format FAT. |
| **st_dev** | Numéro d’entraînement du disque contenant le fichier (même que **st_rdev**). |
| **st_ino** | Nombre du nœud d’information **(l’inode)** pour le fichier (unIX-spécifique). Sur les systèmes de fichiers UNIX, **l’inode** décrit les timbres de date et d’heure du fichier, les autorisations et le contenu. Lorsque les fichiers sont liés les uns aux autres, ils partagent la même **inode**. **L’inode**, et donc **st_ino**, n’a pas de sens dans les systèmes de fichiers FAT, HPFS, ou NTFS. |
| **st_mode** | Masque de bits pour les informations relatives au mode de fichier. Le **_S_IFDIR** bit est réglé si *le chemin* spécifie un répertoire; le **_S_IFREG** bit est réglé si *le chemin* spécifie un fichier ordinaire ou un appareil. Les bits de lecture/écriture utilisateur sont définis en fonction du mode d’autorisation du fichier. Les bits d’exécution utilisateur sont définis en fonction de l’extension de nom de fichier. |
| **st_mtime** | Heure de dernière modification du fichier. |
| **st_nlink** | Toujours 1 sur les systèmes de fichiers autres que NTFS. |
| **st_rdev** | Numéro d’entraînement du disque contenant le fichier (même que **st_dev**). |
| **st_size** | Taille du fichier dans les octets; un intégriste 64 bits pour les variations avec le suffixe **i64.** |
| **st_uid** | Identificateur numérique de l’utilisateur propriétaire du fichier (propre à UNIX). Ce champ est toujours zéro sur les systèmes Windows. Un fichier de redirection est classé comme un fichier Windows. |

Si *le chemin* se réfère à un dispositif, le **st_size**, différents champs de temps, **st_dev,** et les champs **de st_rdev** dans la structure **_stat** sont vides de sens. Étant donné que STAT.H utilise le type [_dev_t](../../c-runtime-library/standard-types.md) défini dans TYPES.H, vous devez inclure TYPES.H avant STAT.H dans votre code.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-têtes facultatifs|
|-------------|---------------------|----------------------|
|**_stat**, **_stat32**, **_stat64**, **_stati64**, **_stat32i64**, **_stat64i32**|\<<sys/types.h> suivi de \<sys/stat.h>|\<errno.h>|
|**_wstat**, **_wstat32**, **_wstat64**, **_wstati64**, **_wstat32i64**, **_wstat64i32**|\<sys/types.h> suivi de \<sys/stat.h> ou \<wchar.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_stat.c
// This program uses the _stat function to
// report information about the file named crt_stat.c.

#include <time.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
   struct _stat buf;
   int result;
   char timebuf[26];
   char* filename = "crt_stat.c";
   errno_t err;

   // Get data associated with "crt_stat.c":
   result = _stat( filename, &buf );

   // Check if statistics are valid:
   if( result != 0 )
   {
      perror( "Problem getting information" );
      switch (errno)
      {
         case ENOENT:
           printf("File %s not found.\n", filename);
           break;
         case EINVAL:
           printf("Invalid parameter to _stat.\n");
           break;
         default:
           /* Should never be reached. */
           printf("Unexpected error in _stat.\n");
      }
   }
   else
   {
      // Output some of the statistics:
      printf( "File size     : %ld\n", buf.st_size );
      printf( "Drive         : %c:\n", buf.st_dev + 'A' );
      err = ctime_s(timebuf, 26, &buf.st_mtime);
      if (err)
      {
         printf("Invalid arguments to ctime_s.");
         exit(1);
      }
      printf( "Time modified : %s", timebuf );
   }
}
```

```Output
File size     : 732
Drive         : C:
Time modified : Thu Feb 07 14:39:36 2002
```

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_setmbcp](setmbcp.md)<br/>
