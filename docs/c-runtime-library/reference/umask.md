---
title: _umask
ms.date: 11/04/2016
api_name:
- _umask
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _umask
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
ms.openlocfilehash: 44614384427b9b70102da03972969c9aa8ef4b83
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957493"
---
# <a name="_umask"></a>_umask

Définit le masque d’autorisation de fichier par défaut. Une version plus sécurisée de cette fonction est disponible. Consultez [_umask_s](umask-s.md).

## <a name="syntax"></a>Syntaxe

```C
int _umask( int pmode );
```

### <a name="parameters"></a>Paramètres

*pmode*<br/>
Paramètre d’autorisation par défaut.

## <a name="return-value"></a>Valeur de retour

**_umask** retourne la valeur précédente de *PMODE*. Aucun retour d'erreur.

## <a name="remarks"></a>Notes

La fonction **_umask** définit le masque d’autorisation de fichier du processus actuel sur le mode spécifié par *PMODE*. Le masque d’autorisation de fichier modifie le paramètre d’autorisation des nouveaux fichiers créés par **_creat**, **_open**ou **_sopen**. Si un bit a la valeur 1 dans le masque, le bit correspondant dans la valeur d’autorisation demandée du fichier prend la valeur 0 (non autorisé). Si un bit a la valeur 0 dans le masque, le bit correspondant est inchangé. Le paramètre d’autorisation d’un nouveau fichier n’est pas défini tant qu’il n’est pas fermé pour la première fois.

L’expression entière *PMODE* contient l’une des constantes manifestes suivantes (ou les deux), définie dans SYS\STAT. Manutention

|*pmode*| |
|-|-|
| **_S_IWRITE** | Écriture autorisée. |
| **_S_IREAD** | Lecture autorisée. |
| **_S_IREAD** &#124; **_S_IWRITE** | Lecture et écriture autorisées. |

Quand les deux constantes sont données, elles sont jointes avec l’opérateur or au **&#124;** niveau du bit (). Si l’argument *PMODE* est **_S_IREAD**, la lecture n’est pas autorisée (le fichier est en écriture seule). Si l’argument *PMODE* est **_S_IWRITE**, l’écriture n’est pas autorisée (le fichier est en lecture seule). Par exemple, si le bit d’écriture est défini dans le masque, les nouveaux fichiers sont en lecture seule. Notez qu’avec les systèmes d’exploitation MS-DOS et Windows, tous les fichiers sont lisibles ; il est impossible d’accorder une autorisation en écriture seule. Par conséquent, la définition du bit de lecture avec **_umask** n’a aucun effet sur les modes du fichier.

Si *PMODE* n’est pas une combinaison de l’une des constantes manifestes ou incorpore un autre ensemble de constantes, la fonction ignore simplement celles-ci.

## <a name="requirements"></a>Configuration requise

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
