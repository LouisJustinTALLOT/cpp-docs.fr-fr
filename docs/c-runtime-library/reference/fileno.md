---
title: _fileno
description: Informations de référence sur l’API pour _fileno ; qui obtient le descripteur de fichier associé à un flux.
ms.date: 4/2/2020
api_name:
- _fileno
- _o__fileno
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
- _fileno
helpviewer_keywords:
- file handles [C++], getting from streams
- fileno function
- _fileno function
- streams, getting file handles
ms.assetid: 86474174-2f17-4100-bcc4-352dd976c7b5
ms.openlocfilehash: c07f446cc3c5c29fb102a74b2b095957589eab46
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554849"
---
# <a name="_fileno"></a>_fileno

Obtient le descripteur de fichier associé à un flux.

## <a name="syntax"></a>Syntaxe

```C
int _fileno(
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*train*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur renvoyée

**_fileno** retourne le descripteur de fichier. Il n’y a pas d’erreur de retour. Le résultat n’est pas défini si *Stream* ne spécifie pas de fichier ouvert. Si Stream a la **valeur null**, **_fileno** appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne -1 et définit **errno** sur **EINVAL**.

Pour plus d’informations sur ces codes d’erreur et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

> [!NOTE]
> Si **stdout** ou **stderr** n’est pas associé à un flux de sortie (par exemple, dans une application Windows sans fenêtre de console), le descripteur de fichier retourné est-2. Dans les versions précédentes, le descripteur de fichier retourné était -1. Cette modification permet aux applications de distinguer cette condition d’une erreur.

## <a name="remarks"></a>Notes

La routine **_fileno** retourne le descripteur de fichier actuellement associé au *flux*. Cette routine est implémentée en tant que fonction et que macro. Pour plus d’informations sur le choix de l’implémentation, consultez [Choix entre fonctions et macros](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête requis|
|--------------|---------------------|
|**_fileno**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_fileno.c
// This program uses _fileno to obtain
// the file descriptor for some standard C streams.
//

#include <stdio.h>

int main( void )
{
   printf( "The file descriptor for stdin is %d\n", _fileno( stdin ) );
   printf( "The file descriptor for stdout is %d\n", _fileno( stdout ) );
   printf( "The file descriptor for stderr is %d\n", _fileno( stderr ) );
}
```

```Output
The file descriptor for stdin is 0
The file descriptor for stdout is 1
The file descriptor for stderr is 2
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
