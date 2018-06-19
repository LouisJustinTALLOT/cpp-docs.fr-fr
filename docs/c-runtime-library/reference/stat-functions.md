---
title: _stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13ce367bdee78be1610a36c887a04f2130375114
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418011"
---
# <a name="stat-stat32-stat64-stati64-stat32i64-stat64i32-wstat-wstat32-wstat64-wstati64-wstat32i64-wstat64i32"></a>_stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32

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

Chacune de ces fonctions retourne 0 si les informations sur l’état des fichiers sont obtenues. Une valeur de retour de -1 indique une erreur, auquel cas **errno** a la valeur **ENOENT**, indiquant que le nom de fichier ou le chemin d’accès est introuvable. La valeur de retour **EINVAL** indique un paramètre non valide ; **errno** est également défini sur **EINVAL** dans ce cas.

Pour plus d’informations sur ce code de retour et sur les autres codes, consultez [_doserrno, errno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

L’horodatage d’un fichier peut être représenté s’il est ultérieur à minuit le 1er janvier 1970 et avant le 23:59:59, le 31 décembre 3000 UTC, sauf si vous utilisez **_stat32** ou **_wstat32**, ou vous avez défini **_ USE_32BIT_TIME_T**, auquel cas la date peut être représentée uniquement jusqu’au 23:59:59 le 18 janvier 2038, UTC.

## <a name="remarks"></a>Notes

Le **_stat** fonction obtient des informations sur le fichier ou le répertoire spécifié par *chemin d’accès* et le stocke dans la structure vers laquelle pointée *tampon*. **_stat** gère automatiquement les arguments de chaîne de caractères multioctets selon le cas, le cas des séquences de caractères multioctets selon la page de codes multioctets en cours d’utilisation.

**_wstat** est une version à caractères larges de **_stat**; le *chemin d’accès* argument **_wstat** est une chaîne à caractères larges. **_wstat** et **_stat** se comportent de façon identique, sauf que **_wstat** ne gère pas les chaînes de caractères multioctets.

Les variantes de ces fonctions prennent en charge les types d’heures 32 ou 64 bits et les longueurs de fichiers 32 ou 64 bits. Le premier suffixe numérique (**32** ou **64**) indique la taille de la durée du type utilisé ; le deuxième suffixe est **i32** ou **i64**, qui indique si la taille du fichier est représentée comme un entier 32 bits ou 64 bits.

**_stat** équivaut à **_stat64i32**, et **struct** **_stat** contient une heure 64 bits. Cela est vrai, sauf si **_USE_32BIT_TIME_T** est défini, auquel cas l’ancien comportement est appliqué. **_stat** utilise une heure 32 bits, et **struct** **_stat** contient une heure 32 bits. Est de même pour **_stati64**.

> [!NOTE]
> **_wstat** ne fonctionne pas avec des liens symboliques de Windows Vista. Dans ce cas, **_wstat** indique toujours une taille de fichier 0. **_stat** ne fonctionne pas correctement avec des liens symboliques.

Cette fonction valide ses paramètres. Si le paramètre *chemin d’accès* ou *tampon* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

### <a name="time-type-and-file-length-type-variations-of-stat"></a>Variantes de type d’heure et de type de longueur de fichier de _stat

|Fonctions|_USE_32BIT_TIME_T défini ?|Type d’heure|Type de longueur de fichier|
|---------------|------------------------------------|---------------|----------------------|
|**_stat**, **_wstat**|Non défini|64 bits|32 bits|
|**_stat**, **_wstat**|Défini|32 bits|32 bits|
|**_stat32**, **_wstat32**|Non affecté par la définition de macro|32 bits|32 bits|
|**_stat64**, **_wstat64**|Non affecté par la définition de macro|64 bits|64 bits|
|**_stati64**, **_wstati64**|Non défini|64 bits|64 bits|
|**_stati64**, **_wstati64**|Défini|32 bits|64 bits|
|**_stat32i64**, **_wstat32i64**|Non affecté par la définition de macro|32 bits|64 bits|
|**_stat64i32**, **_wstat64i32**|Non affecté par la définition de macro|64 bits|32 bits|

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstat**|**_stat**|**_stat**|**_wstat**|
|**_tstat64**|**_stat64**|**_stat64**|**_wstat64**|
|**_tstati64**|**_stati64**|**_stati64**|**_wstati64**|
|**_tstat32i64**|**_stat32i64**|**_stat32i64**|**_wstat32i64**|
|**_tstat64i32**|**_stat64i32**|**_stat64i32**|**_wstat64i32**|

Le **_stat** structure, définie dans SYS\STAT. H, contient les champs suivants.

|Champ||
|-|-|
**st_gid**|Identificateur numérique du groupe propriétaire du fichier (propre à UNIX). Ce champ est toujours zéro sur les systèmes Windows. Un fichier de redirection est classé comme un fichier Windows.
**st_atime**|Heure du dernier accès au fichier. Valide sur NTFS, mais pas sur les lecteurs de disque au format FAT.
**st_ctime**|Heure de création du fichier. Valide sur NTFS, mais pas sur les lecteurs de disque au format FAT.
**st_dev**|Numéro de lecteur du disque contenant le fichier (identique à **st_rdev**).
**st_ino**|Numéro de nœud d’informations (le **inode**) pour le fichier (propre à UNIX). Sur les systèmes de fichiers UNIX, le **inode** décrit le contenu et les horodatages, les autorisations et date du fichier. Lorsque les fichiers sont liées à un autre, ils partagent le même **inode**. Le **inode**et par conséquent **st_ino**, n’a aucune signification dans les systèmes de fichiers FAT, HPFS ou NTFS.
**st_mode**|Masque de bits pour les informations relatives au mode de fichier. Le **_S_IFDIR** bit est défini si *chemin d’accès* spécifie un répertoire ; le **_S_IFREG** bit est défini si *chemin d’accès* spécifie un fichier ordinaire ou un périphérique. Les bits de lecture/écriture utilisateur sont définis en fonction du mode d’autorisation du fichier. Les bits d’exécution utilisateur sont définis en fonction de l’extension de nom de fichier.
**st_mtime**|Heure de dernière modification du fichier.
**st_nlink**|Toujours 1 sur les systèmes de fichiers autres que NTFS.
**st_rdev**|Numéro de lecteur du disque contenant le fichier (identique à **st_dev**).
**st_size**|Taille du fichier en octets ; un entier 64 bits pour les variantes avec le **i64** suffixe.
**st_uid**|Identificateur numérique de l’utilisateur propriétaire du fichier (propre à UNIX). Ce champ est toujours zéro sur les systèmes Windows. Un fichier de redirection est classé comme un fichier Windows.

Si *chemin d’accès* fait référence à un périphérique, le **st_size**, divers champs d’heure, **st_dev**, et **st_rdev** champs dans le **_stat**  structure sont sans effet. Étant donné que STAT.H utilise le type [_dev_t](../../c-runtime-library/standard-types.md) défini dans TYPES.H, vous devez inclure TYPES.H avant STAT.H dans votre code.

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
