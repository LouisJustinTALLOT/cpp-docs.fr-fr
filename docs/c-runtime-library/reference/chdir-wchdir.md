---
title: _chdir, _wchdir
ms.date: 11/04/2016
apiname:
- _wchdir
- _chdir
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
- tchdir
- _chdir
- _wchdir
- _tchdir
- wchdir
helpviewer_keywords:
- _tchdir function
- _chdir function
- _wchdir function
- tchdir function
- wchdir function
- chdir function
- directories [C++], changing
ms.assetid: 85e9393b-62ac-45d5-ab2a-fa2217f6152e
ms.openlocfilehash: e4cf7a44864df0b5ecca531aab3db4546c25bb2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556336"
---
# <a name="chdir-wchdir"></a>_chdir, _wchdir

Change le répertoire de travail actif.

## <a name="syntax"></a>Syntaxe

```C
int _chdir(
   const char *dirname
);
int _wchdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>Paramètres

*nom_répertoire*<br/>
Chemin du nouveau répertoire de travail.

## <a name="return-value"></a>Valeur de retour

Ces fonctions retournent la valeur 0 en cas de réussite. Une valeur de retour de -1 indique un échec. Si le chemin d’accès spécifié est introuvable, **errno** a la valeur **ENOENT**. Si *dirname* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne -1.

## <a name="remarks"></a>Notes

Le **_chdir** fonction modifie le répertoire de travail actuel vers le répertoire spécifié par *dirname*. Le *dirname* paramètre doit faire référence à un répertoire existant. Cette fonction peut changer le répertoire de travail actuel sur n’importe quel lecteur. Si une nouvelle lettre de lecteur n’est spécifiée dans *dirname*, la lettre de lecteur par défaut est également modifiée. Par exemple, si A est la lettre de lecteur par défaut et \BIN le répertoire de travail actuel, l’appel suivant change le répertoire de travail actuel pour le lecteur C et établit C comme nouveau lecteur par défaut :

```C
_chdir("c:\temp");
```

Lorsque vous utilisez le caractère facultatif barre oblique inverse (**&#92;**) dans les chemins d’accès, vous devez placer deux barres obliques inverses (**&#92;&#92;**) dans une chaîne littérale C pour représenter une barre oblique inverse ( **&#92;**).

**_wchdir** est une version à caractères larges de **_chdir**; le *dirname* l’argument de **_wchdir** est une chaîne de caractères larges. **_wchdir** et **_chdir** se comportent de façon identique dans le cas contraire.

### <a name="generic-text-routine-mapping"></a>Mappage de routines de texte générique :

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchdir**|**_chdir**|**_chdir**|**_wchdir**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_chdir**|\<direct.h>|\<errno.h>|
|**_wchdir**|\<direct.h> ou \<wchar.h>|\<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_chdir.c
// arguments: C:\WINDOWS

/* This program uses the _chdir function to verify
   that a given directory exists. */

#include <direct.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( int argc, char *argv[] )
{

   if(_chdir( argv[1] ) )
   {
      switch (errno)
      {
      case ENOENT:
         printf( "Unable to locate the directory: %s\n", argv[1] );
         break;
      case EINVAL:
         printf( "Invalid buffer.\n");
         break;
      default:
         printf( "Unknown error.\n");
      }
   }
   else
      system( "dir *.exe");
}
```

```Output
Volume in drive C has no label.
Volume Serial Number is 2018-08A1

Directory of c:\windows

08/29/2002  04:00 AM         1,004,032 explorer.exe
12/17/2002  04:43 PM            10,752 hh.exe
03/03/2003  09:24 AM            33,792 ieuninst.exe
10/29/1998  04:45 PM           306,688 IsUninst.exe
08/29/2002  04:00 AM            66,048 NOTEPAD.EXE
03/03/2003  09:24 AM            33,792 Q330994.exe
08/29/2002  04:00 AM           134,144 regedit.exe
02/28/2003  06:26 PM            46,352 setdebug.exe
08/29/2002  04:00 AM            15,360 TASKMAN.EXE
08/29/2002  04:00 AM            49,680 twunk_16.exe
08/29/2002  04:00 AM            25,600 twunk_32.exe
08/29/2002  04:00 AM           256,192 winhelp.exe
08/29/2002  04:00 AM           266,752 winhlp32.exe
              13 File(s)      2,249,184 bytes
               0 Dir(s)  67,326,029,824 bytes free
```

## <a name="see-also"></a>Voir aussi

[Contrôle de répertoire](../../c-runtime-library/directory-control.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
