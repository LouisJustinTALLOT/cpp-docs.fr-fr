---
title: _getdcwd_dbg, _wgetdcwd_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _getdcwd_dbg
- _wgetdcwd_dbg
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
apitype: DLLExport
f1_keywords:
- _getdcwd_dbg
- getdcwd_dbg
- _wgetdcwd_dbg
- wgetdcwd_dbg
dev_langs:
- C++
helpviewer_keywords:
- working directory
- _getdcwd_dbg function
- wgetdcwd_dbg function
- current working directory
- getdcwd_dbg function
- _wgetdcwd_dbg function
- directories [C++], current working
ms.assetid: 266bf6f0-0417-497f-963d-2e0f306d9385
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f68fc4fe1c19204433e8f5c9b6c7991d8f7f90e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402824"
---
# <a name="getdcwddbg-wgetdcwddbg"></a>_getdcwd_dbg, _wgetdcwd_dbg

Versions de débogage des fonctions [_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md) (disponibles uniquement durant le débogage).

## <a name="syntax"></a>Syntaxe

```C
char *_getdcwd_dbg(
   int drive,
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetdcwd_dbg(
   int drive,
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Paramètres

*Lecteur*<br/>
Nom du lecteur de disque.

*buffer*<br/>
Emplacement de stockage pour le chemin.

*MAXLEN*<br/>
Longueur maximale du chemin en caractères : **char** pour **_getdcwd_dbg** et **wchar_t** pour **_wgetdcwd_dbg**.

*blockType*<br/>
Type du bloc de mémoire demandé : **_CLIENT_BLOCK** ou **_NORMAL_BLOCK**.

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé l’opération d’allocation ou **NULL**.

*linenumber*<br/>
Numéro de ligne dans le fichier source où l’opération d’allocation a été demandée ou **NULL**.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers *tampon*. A **NULL** valeur renvoyée indique une erreur, et **errno** prend la valeur **ENOMEM**, indiquant que la mémoire est insuffisante pour allouer *maxlen* octets (quand un **NULL** argument n’est fourni en tant que *tampon*), ou à **ERANGE**, indiquant que le chemin d’accès fait plu *maxlen*  caractères. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_getdcwd_dbg** et **_wgetdcwd_dbg** fonctions sont identiques aux **_getdcwd** et **_wgetdcwd** , sauf que, lorsque **_DEBUG** est défini, ces fonctions utilisent la version debug de **malloc** et **_malloc_dbg** pour allouer la mémoire si **NULL** est passé comme le *tampon* paramètre. Pour plus d’informations, consultez [_malloc_dbg](malloc-dbg.md).

Dans la plupart des cas, vous n'avez pas besoin d'appeler ces fonctions de manière explicite. Au lieu de cela, vous pouvez définir le **_CRTDBG_MAP_ALLOC** indicateur. Lorsque **_CRTDBG_MAP_ALLOC** est défini, les appels à **_getdcwd** et **_wgetdcwd** sont remappés à **_getdcwd_dbg** et **_ wgetdcwd_dbg**, respectivement, avec la *blockType* la valeur **_NORMAL_BLOCK**. Par conséquent, il est inutile d’appeler ces fonctions de manière explicite sauf si vous souhaitez marquer les blocs du tas comme **_CLIENT_BLOCK**. Pour plus d’informations, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd_dbg**|**_getdcwd_dbg**|**_getdcwd_dbg**|**_wgetdcwd_dbg**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_getdcwd_dbg**|\<crtdbg.h>|
|**_wgetdcwd_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[Contrôle de répertoire](../../c-runtime-library/directory-control.md)<br/>
[Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
