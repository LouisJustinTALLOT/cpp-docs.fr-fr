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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d590910d5f5092a78ad64c8f9ef0aa259211e226
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362176"
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

*pOldMode (en)*<br/>
Valeur précédente du paramètre d’autorisation.

## <a name="return-value"></a>Valeur de retour

Retourne un code d’erreur si *le mode* ne spécifie pas un mode valide ou le pointeur *pOldMode* est **NULL**.

### <a name="error-conditions"></a>Conditions d'erreur

|*mode*|*pOldMode (en)*|Valeur retournée|Contenu de *pOldMode*|
|------------|----------------|----------------------|--------------------------------|
|n'importe laquelle|**Null**|**EINVAL (EN)**|non modifié|
|mode non valide|n'importe laquelle|**EINVAL (EN)**|non modifié|

Si l’une des conditions ci-dessus se présente, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **_umask_s** renvoie **EINVAL** et met **errno** à **EINVAL**.

## <a name="remarks"></a>Notes

La fonction **_umask_s** définit le masque de l’autorisation de fichier du processus actuel au mode spécifié par *mode*. Le masque d’autorisation de fichier modifie le paramètre d’autorisation de nouveaux fichiers créés par **_creat**, **_open**, ou **_sopen**. Si un bit a la valeur 1 dans le masque, le bit correspondant dans la valeur d’autorisation demandée du fichier prend la valeur 0 (non autorisé). Si un bit a la valeur 0 dans le masque, le bit correspondant est inchangé. Le paramètre d’autorisation d’un nouveau fichier n’est pas défini tant qu’il n’est pas fermé pour la première fois.

L’expression *integer pmode* contient une ou les deux des constantes manifestes suivantes, définies dans SYS-STAT. H:

|*pmode*||
|-|-|
|**_S_IWRITE**|Écriture autorisée.|
|**_S_IREAD**|Lecture autorisée.|
|\| **_S_IREAD _S_IWRITE** **_S_IREAD**|Lecture et écriture autorisées.|

Lorsque les deux constantes sont données, elles sont **|** jointes à l’opérateur bitwise-OR ( ). Si l’argument du *mode* est **_S_IREAD,** la lecture n’est pas autorisée (le fichier est écrit uniquement). Si l’argument du *mode* est **_S_IWRITE,** l’écriture n’est pas autorisée (le fichier est lu uniquement). Par exemple, si le bit d’écriture est défini dans le masque, les nouveaux fichiers sont en lecture seule. Notez qu’avec les systèmes d’exploitation MS-DOS et Windows, tous les fichiers sont lisibles ; il est impossible d’accorder une autorisation en écriture seule. Par conséquent, la définition du bit de lecture avec **_umask_s** n’a aucun effet sur les modes du fichier.

Si *le pmode* n’est pas une combinaison de l’une des constantes manifestes ou intègre un autre ensemble de constantes, la fonction sera tout simplement ignorer ceux-ci.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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
