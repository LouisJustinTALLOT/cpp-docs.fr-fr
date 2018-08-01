---
title: _access_s, _waccess_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _access_s
- _waccess_s
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
- waccess_s
- access_s
- _waccess_s
- _access_s
dev_langs:
- C++
helpviewer_keywords:
- access_s function
- taccess_s function
- _taccess_s function
- waccess_s function
- _access_s function
- _waccess_s function
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82390f7afe45b48539fb5c33130900ef75cf1967
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403301"
---
# <a name="accesss-waccesss"></a>_access_s, _waccess_s

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

*path*  
Chemin du répertoire ou du fichier.

*mode*  
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

Lorsqu’il est utilisé avec des fichiers, le **_access_s** fonction détermine si le fichier spécifié existe et qu’il est accessible comme spécifié par la valeur de *mode*. Lorsqu’il est utilisé avec les répertoires, **_access_s** détermine uniquement si le répertoire spécifié existe. Dans Windows 2000 et les systèmes d’exploitation ultérieurs, tous les répertoires ont lu et l’accès en écriture.

|Valeur du mode|Test réalisé sur le fichier|
|----------------|---------------------|
|00|Existence uniquement.|
|02|Autorisation d’écriture.|
|04|Autorisation de lecture.|
|06|Autorisations de lecture et d’écriture.|

L’autorisation de lecture ou d’écriture dans le fichier n’est pas suffisante pour assurer la possibilité d’ouvrir un fichier. Par exemple, si un fichier est verrouillé par un autre processus, il ne peut pas être accessible même si **_access_s** retourne 0.

**_waccess_s** est une version à caractères larges de **_access_s**, où le *chemin d’accès* l’argument de **_waccess_s** est une chaîne de caractères larges. Sinon, **_waccess_s** et **_access_s** ont un comportement identique.

Ces fonctions valident leurs paramètres. Si *chemin d’accès* est NULL ou *mode* ne spécifie pas un mode valide, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l'exécution est autorisée à se poursuivre, ces fonctions attribuent à `errno` la valeur `EINVAL` et retournent `EINVAL`.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess_s`|**_access_s**|**_access_s**|**_waccess_s**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_access_s**|\<io.h>|\<errno.h>|
|**_waccess_s**|\<wchar.h> ou \<io.h>|\<errno.h>|

## <a name="example"></a>Exemple

Cet exemple utilise **_access_s** pour vérifier si le fichier nommé crt_access_s.c existe et si l’écriture est autorisée.

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

[Gestion de fichiers](../../c-runtime-library/file-handling.md)  
[_access, _waccess](access-waccess.md)  
[_chmod, _wchmod](chmod-wchmod.md)  
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)  
[_open, _wopen](open-wopen.md)  
[_stat, _wstat, fonctions](stat-functions.md)  