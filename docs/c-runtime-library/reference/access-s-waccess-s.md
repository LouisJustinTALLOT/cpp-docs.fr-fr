---
title: _access_s, _waccess_s
ms.date: 4/2/2020
api_name:
- _access_s
- _waccess_s
- _o__access_s
- _o__waccess_s
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
- waccess_s
- access_s
- _waccess_s
- _access_s
helpviewer_keywords:
- access_s function
- taccess_s function
- _taccess_s function
- waccess_s function
- _access_s function
- _waccess_s function
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
ms.openlocfilehash: 7f16951b99eb29bcb8c39499c29be1018cb86616
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349127"
---
# <a name="_access_s-_waccess_s"></a>_access_s, _waccess_s

Détermine les autorisations de lecture/écriture de fichier. Il s’agit d’une version de [_access, _waccess](access-waccess.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _access_s(
   const char *path,
   int mode
);
errno_t _waccess_s(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>Paramètres

*path*<br/>
Chemin du répertoire ou du fichier.

*mode*<br/>
Paramètre d'autorisation.

## <a name="return-value"></a>Valeur de retour

Chaque fonction retourne 0 si le fichier a le mode donné. La fonction retourne un code d’erreur si le fichier nommé n’existe pas ou qu’il est inaccessible dans le mode donné. Dans ce cas, la fonction retourne un code d’erreur de l’ensemble suivant et définit également `errno` sur la même valeur.

|Valeur de la variable errno|Condition|
|-|-|
`EACCES`|Accès refusé. Le paramètre d’autorisation du fichier n’autorise pas l’accès spécifié.
`ENOENT`|Chemin ou nom de fichier introuvable.
`EINVAL`|Paramètre non valide.

Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Lorsqu’il est utilisé avec des fichiers, la fonction **_access_s** détermine si le fichier spécifié existe et peut être consulté comme spécifié par la valeur du *mode*. Lorsqu’il est utilisé avec des répertoires, **_access_s** détermine seulement si l’annuaire spécifié existe. Dans Windows 2000 et plus tard les systèmes d’exploitation, tous les répertoires ont lu et écrit l’accès.

|Valeur du mode|Test réalisé sur le fichier|
|----------------|---------------------|
|00|Existence uniquement.|
|02|Autorisation d’écriture.|
|04|Autorisation de lecture.|
|06|Autorisations de lecture et d’écriture.|

L’autorisation de lecture ou d’écriture dans le fichier n’est pas suffisante pour assurer la possibilité d’ouvrir un fichier. Par exemple, si un fichier est verrouillé par un autre processus, il peut ne pas être accessible même si **_access_s** renvois 0.

**_waccess_s** est une version à caractère large de **_access_s**, où l’argument *de chemin* à **_waccess_s** est une chaîne de caractère large. Sinon, **_waccess_s** et **_access_s** se comportent de façon identique.

Ces fonctions valident leurs paramètres. Si *le chemin* est NULL ou si le *mode* ne spécifie pas un mode valide, le gestionnaire de paramètres invalide est invoqué, tel que décrit dans La validation [des paramètres](../../c-runtime-library/parameter-validation.md). Si l'exécution est autorisée à se poursuivre, ces fonctions attribuent à `errno` la valeur `EINVAL` et retournent `EINVAL`.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess_s`|**_access_s**|**_access_s**|**_waccess_s**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_access_s**|\<io.h>|\<errno.h>|
|**_waccess_s**|\<wchar.h> ou \<io.h>|\<errno.h>|

## <a name="example"></a>Exemple

Cet exemple utilise **_access_s** pour vérifier le fichier nommé crt_access_s.c pour voir s’il existe et si l’écriture est autorisée.

```C
// crt_access_s.c

#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    errno_t err = 0;

    // Check for existence.
    if ((err = _access_s( "crt_access_s.c", 0 )) == 0 )
    {
        printf_s( "File crt_access_s.c exists.\n" );

        // Check for write permission.
        if ((err = _access_s( "crt_access_s.c", 2 )) == 0 )
        {
            printf_s( "File crt_access_s.c does have "
                      "write permission.\n" );
        }
        else
        {
            printf_s( "File crt_access_s.c does not have "
                      "write permission.\n" );
        }
    }
    else
    {
        printf_s( "File crt_access_s.c does not exist.\n" );
    }
}
```

```Output
File crt_access_s.c exists.
File crt_access_s.c does not have write permission.
```

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat, fonctions](stat-functions.md)
