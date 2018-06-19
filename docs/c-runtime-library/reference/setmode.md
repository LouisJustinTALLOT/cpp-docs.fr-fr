---
title: _setmode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _setmode
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
- _setmode
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59aed27ec4803cd1709635da44ef37d748342e29
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407494"
---
# <a name="setmode"></a>_setmode

Définit le mode de traduction des fichiers.

## <a name="syntax"></a>Syntaxe

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>Paramètres

*fd*<br/>
Descripteur de fichier.

*mode*<br/>
Nouveau mode de traduction.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne le mode de traduction précédent.

Si des paramètres non valides sont passés à cette fonction, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne -1 et affecte **errno** soit **EBADF**, ce qui indique un descripteur de fichier non valide, ou **EINVAL**, qui Indique un non valide *mode* argument.

Pour plus d'informations sur ces codes de retour et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_setmode** fonction affecte *mode* le mode de traduction de fichier spécifié par *fd*. Passage **_O_TEXT** en tant que *mode* définit le texte (autrement dit, traduit) mode. Combinaisons chariot retour-ligne (CRLF) sont traduites en une seule ligne dans l’entrée de flux de caractères. Les caractères de saut de ligne sont traduits en combinaisons retour chariot/saut de ligne en sortie. Passage **_O_BINARY** définit binaire (non traduit) le mode, dans lequel ces traductions sont supprimées.

Vous pouvez également passer **_O_U16TEXT**, **_O_U8TEXT**, ou **_O_WTEXT** pour activer le mode Unicode, comme illustré dans le deuxième exemple plus loin dans ce document. **_setmode** est généralement utilisé pour modifier le mode de traduction par défaut de **stdin** et **stdout**, mais vous pouvez l’utiliser sur n’importe quel fichier. Si vous appliquez **_setmode** au descripteur de fichier pour un flux de données, appelez **_setmode** avant d’effectuer toutes les opérations sur le flux d’entrée ou de sortie.

> [!CAUTION]
> Si vous écrivez des données dans un flux de fichier explicitement vider le code à l’aide de [fflush](fflush.md) avant d’utiliser **_setmode** pour modifier le mode. Si vous ne videz pas le code, un comportement inattendu peut se produire. Si vous n'avez pas écrit de données dans le flux, vous n'avez pas à vider le code.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-têtes facultatifs|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

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

## <a name="example"></a>Exemple

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
