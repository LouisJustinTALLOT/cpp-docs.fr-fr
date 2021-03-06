---
description: 'En savoir plus sur : _setmode'
title: _setmode
ms.date: 4/2/2020
api_name:
- _setmode
- _o__setmode
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
- _setmode
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
ms.openlocfilehash: 305e9a247410d762821ed0e3e004505adc1a4034
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146378"
---
# <a name="_setmode"></a>_setmode

Définit le mode de traduction des fichiers.

## <a name="syntax"></a>Syntaxe

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>Paramètres

*FD*<br/>
Descripteur de fichier.

*mode*<br/>
Nouveau mode de traduction.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, retourne le mode de traduction précédent.

Si des paramètres non valides sont passés à cette fonction, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne-1 et affecte à **errno** la valeur **EBADF**, qui indique un descripteur de fichier non valide ou **EINVAL**, qui indique un argument *mode* non valide.

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_setmode** *définit le mode de traduction du fichier* donné par *FD*. Le passage de **_O_TEXT** en *mode* définit le mode texte (autrement dit, traduit). Les combinaisons retour chariot-saut de ligne sont traduites en un seul caractère de saut de ligne en entrée. Les caractères de saut de ligne sont traduits en combinaisons retour chariot/saut de ligne en sortie. Le passage de **_O_BINARY** définit le mode binaire (non traduit), dans lequel ces traductions sont supprimées.

Vous pouvez également passer **_O_U16TEXT**, **_O_U8TEXT** ou **_O_WTEXT** pour activer le mode Unicode, comme illustré dans le deuxième exemple plus loin dans ce document.

> [!CAUTION]
> Le mode Unicode est destiné aux fonctions d’impression larges (par exemple, `wprintf` ) et n’est pas pris en charge pour les fonctions d’impression étroite. L’utilisation d’une fonction d’impression étroite sur un flux en mode Unicode déclenche une assertion.

**_setmode** est généralement utilisé pour modifier le mode de traduction par défaut de **stdin** et **stdout**, mais vous pouvez l’utiliser sur n’importe quel fichier. Si vous appliquez **_setmode** au descripteur de fichier pour un flux, appelez **_setmode** avant d’effectuer des opérations d’entrée ou de sortie sur le flux.

> [!CAUTION]
> Si vous écrivez des données dans un flux de fichier, videz explicitement le code à l’aide de [fflush](fflush.md) avant d’utiliser **_setmode** pour modifier le mode. Si vous ne videz pas le code, un comportement inattendu peut se produire. Si vous n'avez pas écrit de données dans le flux, vous n'avez pas à vider le code.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-têtes facultatifs|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example-use-_setmode-to-change-stdin"></a>Exemple : utiliser _setmode pour modifier stdin

```C
// crt_setmode.c
// This program uses _setmode to change
// stdin from text mode to binary mode.

#include <stdio.h>
#include <fcntl.h>
#include <io.h>

int main( void )
{
   int result;

   // Set "stdin" to have binary mode:
   result = _setmode( _fileno( stdin ), _O_BINARY );
   if( result == -1 )
      perror( "Cannot set mode" );
   else
      printf( "'stdin' successfully changed to binary mode\n" );
}
```

```Output
'stdin' successfully changed to binary mode
```

## <a name="example-use-_setmode-to-change-stdout"></a>Exemple : utiliser _setmode pour modifier stdout

```C
// crt_setmodeunicode.c
// This program uses _setmode to change
// stdout to Unicode. Cyrillic and Ideographic
// characters will appear on the console (if
// your console font supports those character sets).

#include <fcntl.h>
#include <io.h>
#include <stdio.h>

int main(void) {
    _setmode(_fileno(stdout), _O_U16TEXT);
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");
    return 0;
}
```

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_set_fmode](set-fmode.md)<br/>
