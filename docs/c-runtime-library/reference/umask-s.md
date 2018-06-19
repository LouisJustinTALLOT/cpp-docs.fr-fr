---
title: _umask_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _umask_s
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
- unmask_s
- _umask_s
dev_langs:
- C++
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d45cb3ded6fd2c3d7a380069a7d7f3fd79619810
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414478"
---
# <a name="umasks"></a>_umask_s

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

Retourne un code d’erreur si *mode* ne spécifie pas un mode valide ou le *pOldMode* pointeur est **NULL**.

### <a name="error-conditions"></a>Conditions d’erreur

|*mode*|*pOldMode*|Valeur de retour|Contenu de *pOldMode*|
|------------|----------------|----------------------|--------------------------------|
|any|**NULL**|**EINVAL**|non modifié|
|mode non valide|any|**EINVAL**|non modifié|

Si l’une des conditions ci-dessus se présente, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **_umask_s** retourne **EINVAL** et définit **errno** à **EINVAL**.

## <a name="remarks"></a>Notes

Le **_umask_s** fonction définit le masque d’autorisation de fichier du processus en cours pour le mode spécifié par *mode*. Le masque d’autorisation de fichier modifie le paramètre d’autorisation de nouveaux fichiers créés par **_creat**, **_open**, ou **_sopen**. Si un bit a la valeur 1 dans le masque, le bit correspondant dans la valeur d’autorisation demandée du fichier prend la valeur 0 (non autorisé). Si un bit a la valeur 0 dans le masque, le bit correspondant est inchangé. Le paramètre d’autorisation d’un nouveau fichier n’est pas défini tant qu’il n’est pas fermé pour la première fois.

L’expression d’entier *pmode* contient une ou les deux constantes de manifeste suivantes, définies dans SYS\STAT. H :

|*pmode*||
|-|-|
|**_S_IWRITE**|Écriture autorisée.|
|**_S_IREAD**|Lecture autorisée.|
|**_S_IREAD** \| **_S_IWRITE**|Lecture et écriture autorisées.|

Lorsque les deux constantes sont données, elles sont jointes avec l’opérateur OR au niveau du bit ( **|** ). Si le *mode* argument est **_S_IREAD**, la lecture n’est pas autorisée (le fichier est en écriture seule). Si le *mode* argument est **_S_IWRITE**, l’écriture n’est pas autorisée (le fichier est en lecture seule). Par exemple, si le bit d’écriture est défini dans le masque, les nouveaux fichiers sont en lecture seule. Notez qu’avec les systèmes d’exploitation MS-DOS et Windows, tous les fichiers sont lisibles ; il est impossible d’accorder une autorisation en écriture seule. Par conséquent, si la lecture de type bit avec **_umask_s** n’a aucun effet sur les modes du fichier.

Si *pmode* n’est pas une combinaison de l’une des constantes de manifeste ou incorpore un autre jeu de constantes, la fonction ignore simplement les.

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
[E/S de bas niveau](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_umask](umask.md)<br/>
