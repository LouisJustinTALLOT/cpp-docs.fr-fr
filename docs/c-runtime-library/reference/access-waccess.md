---
title: _access, _waccess
ms.date: 4/2/2020
api_name:
- _access
- _waccess
- _o__access
- _o__waccess
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _waccess
- _access
- taccess
- waccess
- _taccess
helpviewer_keywords:
- access function
- _taccess function
- waccess function
- _access function
- _waccess function
- taccess function
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
ms.openlocfilehash: fdada7f02115f44aa6a7e3c5e9bdfdf5e65f8b2f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846587"
---
# <a name="_access-_waccess"></a>_access, _waccess

Détermine si un fichier est en lecture seule ou non. Des versions plus sécurisées sont disponibles. Consultez [_access_s, _waccess_s](access-s-waccess-s.md).

## <a name="syntax"></a>Syntaxe

```C
int _access(
   const char *path,
   int mode
);
int _waccess(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>Paramètres

*path*<br/>
Chemin du répertoire ou du fichier.

*mode*<br/>
Attribut de lecture/écriture.

## <a name="return-value"></a>Valeur renvoyée

Chaque fonction retourne 0 si le fichier a le mode donné. La fonction retourne-1 si le fichier nommé n’existe pas ou s’il n’a pas le mode donné ; dans ce cas, `errno` est défini comme indiqué dans le tableau suivant.

| Valeur | Description |
|--|--|
| `EACCES` | Accès refusé : le paramètre d’autorisation du fichier n’autorise pas l’accès spécifié. |
| `ENOENT` | Chemin ou nom de fichier introuvable. |
| `EINVAL` | Paramètre non valide. |

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Lorsqu’elle est utilisée avec des fichiers, la fonction **_access** détermine si le fichier ou le répertoire spécifié existe et possède les attributs spécifiés par la valeur de *mode*. En cas d’utilisation avec des répertoires, **_access** détermine uniquement si le répertoire spécifié existe ; dans les systèmes d’exploitation Windows 2000 et versions ultérieures, tous les répertoires disposent d’un accès en lecture et en écriture.

|valeur du *mode*|Test réalisé sur le fichier|
|------------------|---------------------|
|00|Existence uniquement|
|02|Écriture seule|
|04|Lecture seule|
|06|Lecture et écriture|

Cette fonction vérifie uniquement si le fichier et le répertoire sont en lecture seule ou non ; elle ne vérifie pas les paramètres de sécurité du système de fichiers. Pour cela, vous avez besoin d’un jeton d’accès. Pour plus d’informations sur la sécurité du système de fichiers, consultez [Access Tokens](/windows/win32/SecAuthZ/access-tokens) (Jetons d’accès). Il existe une classe ATL pour fournir cette fonctionnalité ; consultez [CAccessToken, classe](../../atl/reference/caccesstoken-class.md).

**_waccess** est une version à caractères larges de **_access**; l’argument *path* de **_waccess** est une chaîne de caractères larges. dans le cas contraire, **_waccess** et **_access** se comportent de la même façon.

Cette fonction valide ses paramètres. Si *path* a la valeur null ou que le *mode* ne spécifie pas de mode valide, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, la fonction définit `errno` avec la valeur `EINVAL` et retourne -1.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess`|**_access**|**_access**|**_waccess**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-têtes facultatifs|
|-------------|---------------------|----------------------|
|**_access**|\<io.h>|\<errno.h>|
|**_waccess**|\<wchar.h> ou \<io.h>|\<errno.h>|

## <a name="example"></a>Exemple

L’exemple suivant utilise **_access** pour vérifier le fichier nommé crt_ACCESS. C pour voir s’il existe et si l’écriture est autorisée.

```C
// crt_access.c
// compile with: /W1
// This example uses _access to check the file named
// crt_ACCESS.C to see if it exists and if writing is allowed.

#include  <io.h>
#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    // Check for existence.
    if( (_access( "crt_ACCESS.C", 0 )) != -1 )
    {
        printf_s( "File crt_ACCESS.C exists.\n" );

        // Check for write permission.
        // Assume file is read-only.
        if( (_access( "crt_ACCESS.C", 2 )) == -1 )
            printf_s( "File crt_ACCESS.C does not have write permission.\n" );
    }
}
```

```Output
File crt_ACCESS.C exists.
File crt_ACCESS.C does not have write permission.
```

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat, fonctions](stat-functions.md)
