---
title: _umask
ms.date: 4/2/2020
api_name:
- _umask
- _o__umask
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
- _umask
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
ms.openlocfilehash: b451f979f2925a31f5baaac52351c5d2c0a76da0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362024"
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

**_umask** retourne la valeur précédente de *pmode*. Aucun retour d'erreur.

## <a name="remarks"></a>Notes

La fonction **_umask** définit le masque de fichier-autorisation du processus actuel au mode spécifié par *pmode*. Le masque d’autorisation de fichier modifie le paramètre d’autorisation de nouveaux fichiers créés par **_creat**, **_open**, ou **_sopen**. Si un bit a la valeur 1 dans le masque, le bit correspondant dans la valeur d’autorisation demandée du fichier prend la valeur 0 (non autorisé). Si un bit a la valeur 0 dans le masque, le bit correspondant est inchangé. Le paramètre d’autorisation d’un nouveau fichier n’est pas défini tant qu’il n’est pas fermé pour la première fois.

L’expression *integer pmode* contient une ou les deux des constantes manifestes suivantes, définies dans SYS-STAT. H:

|*pmode*| |
|-|-|
| **_S_IWRITE** | Écriture autorisée. |
| **_S_IREAD** | Lecture autorisée. |
| **_S_IREAD** **_S_IWRITE** &#124; | Lecture et écriture autorisées. |

Lorsque les deux constantes sont données, elles sont jointes à l’opérateur bitwise-OR **(&#124;).** Si l’argument *du pmode* est **_S_IREAD,** la lecture n’est pas autorisée (le fichier est écrit uniquement). Si l’argument *du pmode* est **_S_IWRITE,** l’écriture n’est pas autorisée (le fichier est lu uniquement). Par exemple, si le bit d’écriture est défini dans le masque, les nouveaux fichiers sont en lecture seule. Notez qu’avec les systèmes d’exploitation MS-DOS et Windows, tous les fichiers sont lisibles ; il est impossible d’accorder une autorisation en écriture seule. Par conséquent, la définition du bit de lecture avec **_umask** n’a aucun effet sur les modes du fichier.

Si *le pmode* n’est pas une combinaison de l’une des constantes manifestes ou intègre un autre ensemble de constantes, la fonction sera tout simplement ignorer ceux-ci.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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
[E/S niveau bas](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
