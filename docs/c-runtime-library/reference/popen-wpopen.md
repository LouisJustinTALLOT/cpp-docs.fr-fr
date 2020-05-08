---
title: _popen, _wpopen
description: Une référence pour les fonctions _popen de la bibliothèque Microsoft C Runtime (CRT _wpopen) et.
ms.date: 4/2/2020
api_name:
- _popen
- _wpopen
- _o__popen
- _o__wpopen
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tpopen
- popen
- wpopen
- _popen
- _wpopen
- _tpopen
helpviewer_keywords:
- tpopen function
- pipes, creating
- _popen function
- _tpopen function
- popen function
- wpopen function
- _wpopen function
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
no-loc:
- _popen
- _wpopen
- _tpopen
- _doserrno
- errno
- _sys_errlist
- _sys_nerr
- EINVAL
ms.openlocfilehash: 37e5bb491234e46a0e3330bc2fd42c16e54793fc
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915288"
---
# <a name="_popen-_wpopen"></a>_popen, _wpopen

Crée un canal et exécute une commande.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
FILE *_popen(
    const char *command,
    const char *mode
);
FILE *_wpopen(
    const wchar_t *command,
    const wchar_t *mode
);
```

### <a name="parameters"></a>Paramètres

*commande*\
Commande à exécuter.

*mode*\
Mode du flux retourné.

## <a name="return-value"></a>Valeur retournée

Retourne un flux associé à une extrémité du canal créé. L’autre extrémité du canal est associée à l’entrée ou à la sortie standard de la commande générée. Les fonctions retournent la valeur **NULL** en cas d’erreur. Si l’erreur est provoquée par un paramètre non valide, **errno** a la valeur **EINVAL**. Consultez la section Notes pour en savoir plus sur les modes valides.

Pour obtenir des informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes 

La fonction **_popen** crée un canal. Il exécute ensuite de manière asynchrone une copie générée du processeur de commandes et utilise la *commande* comme ligne de commande. La chaîne de caractères *mode* spécifie le type d’accès demandé, comme suit.

|Mode d’accès|Description|
|-|-|
|**r**|Le processus appelant peut lire la sortie standard de la commande générée en utilisant le flux retourné.|
|**s**|Le processus appelant peut écrire dans l’entrée standard de la commande générée en utilisant le flux retourné.|
|**p**|Ouvre en mode binaire.|
|**t**|Ouvre en mode texte.|

> [!NOTE]
> Si elle est utilisée dans un programme Windows, la fonction **_popen** retourne un pointeur de fichier non valide qui amène le programme à cesser de répondre indéfiniment. **_popen** fonctionne correctement dans une application console. Pour créer une application Windows qui redirige l’entrée et la sortie, consultez [création d’un processus enfant avec une entrée et une sortie redirigées](/windows/win32/ProcThread/creating-a-child-process-with-redirected-input-and-output) dans le SDK Windows.

**_wpopen** est une version à caractères larges de **_popen**; l’argument *path* de **_wpopen** est une chaîne de caractères larges. dans le cas contraire, **_wpopen** et **_popen** se comportent de la même façon.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_popen**|\<stdio.h>|
|**_wpopen**|\<stdio.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a> Exemple

```C
// crt_popen.c
/* This program uses _popen and _pclose to receive a
* stream of text from a system process.
*/

#include <stdio.h>
#include <stdlib.h>

int main( void )
{

   char   psBuffer[128];
   FILE   *pPipe;

        /* Run DIR so that it writes its output to a pipe. Open this
         * pipe with read text attribute so that we can read it
         * like a text file.
         */

   if( (pPipe = _popen( "dir *.c /on /p", "rt" )) == NULL )
      exit( 1 );

   /* Read pipe until end of file, or an error occurs. */

   while(fgets(psBuffer, 128, pPipe))
   {
      puts(psBuffer);
   }

   /* Close pipe and print return value of pPipe. */
   if (feof( pPipe))
   {
     printf( "\nProcess returned %d\n", _pclose( pPipe ) );
   }
   else
   {
     printf( "Error: Failed to read the pipe to the end.\n");
   }
}
```

Cette sortie suppose qu’il n’y a qu’un seul fichier dans le répertoire actif `.c` qui a une extension de nom de fichier.

```Output
Volume in drive C is CDRIVE
Volume Serial Number is 0E17-1702

Directory of D:\proj\console\test1

07/17/98  07:26p                   780 popen.c
               1 File(s)            780 bytes
                             86,597,632 bytes free

Process returned 0
```

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)\
[_pclose](pclose.md)\
[_pipe](pipe.md)
