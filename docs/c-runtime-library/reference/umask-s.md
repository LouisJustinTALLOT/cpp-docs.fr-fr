---
title: _umask_s
ms.date: 4/2/2020
api_name:
- _umask_s
- _o__umask_s
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
- unmask_s
- _umask_s
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
ms.openlocfilehash: 712313314c67d15987326e3e3a920cd5f1039239
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913888"
---
# <a name="_umask_s"></a>_umask_s

Définit le masque d’autorisation de fichier par défaut. Version de [_umask](umask.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _umask_s(
   int mode,
   int * pOldMode
);
```

### <a name="parameters"></a>Paramètres

*mode*<br/>
Paramètre d’autorisation par défaut.

*pOldMode*<br/>
Valeur précédente du paramètre d’autorisation.

## <a name="return-value"></a>Valeur de retour

Retourne un code d’erreur si le *mode* ne spécifie pas de mode valide ou si le pointeur *POldMode* a la **valeur null**.

### <a name="error-conditions"></a>Conditions d'erreur

|*mode*|*pOldMode*|Valeur retournée|Contenu de *pOldMode*|
|------------|----------------|----------------------|--------------------------------|
|n'importe laquelle|**NUL**|**EINVAL**|non modifié|
|mode non valide|n'importe laquelle|**EINVAL**|non modifié|

Si l’une des conditions ci-dessus se présente, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **_umask_s** retourne **EINVAL** et définit **errno** sur **EINVAL**.

## <a name="remarks"></a>Notes 

La fonction **_umask_s** définit le masque d’autorisation de fichier du processus en cours sur le mode spécifié par *mode*. Le masque d’autorisation de fichier modifie le paramètre d’autorisation des nouveaux fichiers créés par **_creat**, **_open**ou **_sopen**. Si un bit a la valeur 1 dans le masque, le bit correspondant dans la valeur d’autorisation demandée du fichier prend la valeur 0 (non autorisé). Si un bit a la valeur 0 dans le masque, le bit correspondant est inchangé. Le paramètre d’autorisation d’un nouveau fichier n’est pas défini tant qu’il n’est pas fermé pour la première fois.

L’expression entière *PMODE* contient l’une des constantes manifestes suivantes (ou les deux), définie dans SYS\STAT. Manutention

|*pmode*||
|-|-|
|**_S_IWRITE**|Écriture autorisée.|
|**_S_IREAD**|Lecture autorisée.|
|**_S_IREAD** \| **_S_IWRITE**|Lecture et écriture autorisées.|

Quand les deux constantes sont données, elles sont jointes avec l’opérateur or au **|** niveau du bit (). Si l’argument de *mode* est **_S_IREAD**, la lecture n’est pas autorisée (le fichier est en écriture seule). Si l’argument de *mode* est **_S_IWRITE**, l’écriture n’est pas autorisée (le fichier est en lecture seule). Par exemple, si le bit d’écriture est défini dans le masque, les nouveaux fichiers sont en lecture seule. Notez qu’avec les systèmes d’exploitation MS-DOS et Windows, tous les fichiers sont lisibles ; il est impossible d’accorder une autorisation en écriture seule. Par conséquent, la définition du bit de lecture avec **_umask_s** n’a aucun effet sur les modes du fichier.

Si *PMODE* n’est pas une combinaison de l’une des constantes manifestes ou incorpore un autre ensemble de constantes, la fonction ignore simplement celles-ci.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_umask_s**|\<io.h>, \<sys/stat.h> et \<sys/types.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_umask_s.c
/* This program uses _umask_s to set
* the file-permission mask so that all future
* files will be created as read-only files.
* It also displays the old mask.
*/

#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask, err;

   /* Create read-only files: */
   err = _umask_s( _S_IWRITE, &oldmask );
   if (err)
   {
      printf("Error setting the umask.\n");
      exit(1);
   }
   printf( "Oldmask = 0x%.4x\n", oldmask );
}
```

```Output
Oldmask = 0x0000
```

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[E/S niveau bas](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_umask](umask.md)<br/>
