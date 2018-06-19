---
title: _umask | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _umask
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
- _umask
dev_langs:
- C++
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce3053bfb19cc81dff15d41d1b5bc6d405da619f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412613"
---
# <a name="umask"></a>_umask

Définit le masque d’autorisation de fichier par défaut. Une version plus sécurisée de cette fonction est disponible. Consultez [_umask_s](umask-s.md).

## <a name="syntax"></a>Syntaxe

```C
int _umask( int pmode );
```

### <a name="parameters"></a>Paramètres

*pmode*<br/>
Paramètre d’autorisation par défaut.

## <a name="return-value"></a>Valeur de retour

**_umask** retourne la valeur précédente de *pmode*. Aucun retour d'erreur.

## <a name="remarks"></a>Notes

Le **_umask** fonction définit le masque d’autorisation de fichier du processus en cours pour le mode spécifié par *pmode*. Le masque d’autorisation de fichier modifie le paramètre d’autorisation de nouveaux fichiers créés par **_creat**, **_open**, ou **_sopen**. Si un bit a la valeur 1 dans le masque, le bit correspondant dans la valeur d’autorisation demandée du fichier prend la valeur 0 (non autorisé). Si un bit a la valeur 0 dans le masque, le bit correspondant est inchangé. Le paramètre d’autorisation d’un nouveau fichier n’est pas défini tant qu’il n’est pas fermé pour la première fois.

L’expression d’entier *pmode* contient une ou les deux constantes de manifeste suivantes, définies dans SYS\STAT. H :

|*pmode*||
|-|-|
**_S_IWRITE**|Écriture autorisée.
**_S_IREAD**|Lecture autorisée.
**_S_IREAD** \| **_S_IWRITE**|Lecture et écriture autorisées.

Lorsque les deux constantes sont données, elles sont jointes avec l’opérateur OR au niveau du bit ( **|** ). Si le *pmode* argument est **_S_IREAD**, la lecture n’est pas autorisée (le fichier est en écriture seule). Si le *pmode* argument est **_S_IWRITE**, l’écriture n’est pas autorisée (le fichier est en lecture seule). Par exemple, si le bit d’écriture est défini dans le masque, les nouveaux fichiers sont en lecture seule. Notez qu’avec les systèmes d’exploitation MS-DOS et Windows, tous les fichiers sont lisibles ; il est impossible d’accorder une autorisation en écriture seule. Par conséquent, si la lecture de type bit avec **_umask** n’a aucun effet sur les modes du fichier.

Si *pmode* n’est pas une combinaison de l’une des constantes de manifeste ou incorpore un autre jeu de constantes, la fonction ignore simplement les.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_umask**|\<io.h>, \<sys/stat.h>, \<sys/types.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_umask.c
// compile with: /W3
// This program uses _umask to set
// the file-permission mask so that all future
// files will be created as read-only files.
// It also displays the old mask.
#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask;

   /* Create read-only files: */
   oldmask = _umask( _S_IWRITE ); // C4996
   // Note: _umask is deprecated; consider using _umask_s instead
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
