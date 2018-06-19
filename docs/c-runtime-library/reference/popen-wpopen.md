---
title: _popen, _wpopen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _popen
- _wpopen
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tpopen
- popen
- wpopen
- _popen
- _wpopen
- _tpopen
dev_langs:
- C++
helpviewer_keywords:
- tpopen function
- pipes, creating
- _popen function
- _tpopen function
- popen function
- wpopen function
- _wpopen function
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a7764e15b18249a9ee3ddd452ae792c8ad172f3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404478"
---
# <a name="popen-wpopen"></a>_popen, _wpopen

Crée un canal et exécute une commande.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*command*<br/>
Commande à exécuter.

*mode*<br/>
Mode du flux retourné.

## <a name="return-value"></a>Valeur de retour

Retourne un flux associé à une extrémité du canal créé. L’autre extrémité du canal est associée à l’entrée ou à la sortie standard de la commande générée. Les fonctions retournent la valeur **NULL** en cas d’erreur. Si l’erreur est un paramètre non valide, par exemple si *commande* ou *mode* est un pointeur null, ou *mode* n’est pas un mode valide, **errno** a la valeur **EINVAL**. Consultez la section Notes pour en savoir plus sur les modes valides.

Pour obtenir des informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_popen** fonction crée un canal de communication et exécute une copie engendrée de l’interpréteur de commandes avec la chaîne spécifiée de manière asynchrone *commande*. La chaîne de caractères *mode* spécifie le type d’accès demandé, comme suit.

**« r »** le processus appelant peut lire la sortie standard de la commande généré à l’aide du flux retourné.

**« w »** le processus appelant peut écrire à l’entrée standard de la commande généré à l’aide du flux retourné.

**« b »** ouvert en mode binaire.

**« t »** ouvert en mode texte.

> [!NOTE]
> Si utilisé dans un programme Windows, le **_popen** fonction retourne un pointeur de fichier non valide, le programme se bloquer indéfiniment. **_popen** fonctionne correctement dans une application console. Pour créer une application Windows qui redirige les entrées et sorties, consultez [création d’un processus enfant avec redirigé d’entrée et sortie](http://msdn.microsoft.com/library/windows/desktop/ms682499) dans le Kit de développement logiciel Windows.

**_wpopen** est une version à caractères larges de **_popen**; le *chemin d’accès* argument **_wpopen** est une chaîne à caractères larges. **_wpopen** et **_popen** comportent de façon identique.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_popen**|\<stdio.h>|
|**_wpopen**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

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
      printf(psBuffer);
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

### <a name="sample-output"></a>Résultat de l'exemple

Cette sortie suppose la présence d’un seul fichier dans le répertoire actuel avec une extension de nom de fichier .c.

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

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pclose](pclose.md)<br/>
[_pipe](pipe.md)<br/>
