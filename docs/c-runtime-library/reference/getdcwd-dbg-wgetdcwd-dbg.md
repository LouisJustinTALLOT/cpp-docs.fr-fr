---
title: _getdcwd_dbg, _wgetdcwd_dbg
ms.date: 11/04/2016
api_name:
- _getdcwd_dbg
- _wgetdcwd_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getdcwd_dbg
- getdcwd_dbg
- _wgetdcwd_dbg
- wgetdcwd_dbg
helpviewer_keywords:
- working directory
- _getdcwd_dbg function
- wgetdcwd_dbg function
- current working directory
- getdcwd_dbg function
- _wgetdcwd_dbg function
- directories [C++], current working
ms.assetid: 266bf6f0-0417-497f-963d-2e0f306d9385
ms.openlocfilehash: 8eb22f3716102c1b63b483e493eb44ac99228004
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955228"
---
# <a name="_getdcwd_dbg-_wgetdcwd_dbg"></a>_getdcwd_dbg, _wgetdcwd_dbg

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

*drive*<br/>
Nom du lecteur de disque.

*buffer*<br/>
Emplacement de stockage pour le chemin.

*maxlen*<br/>
Longueur maximale du chemin d’accès en caractères : **char** pour **_getdcwd_dbg** et **wchar_t** pour **_wgetdcwd_dbg**.

*blockType*<br/>
Type demandé du bloc de mémoire : _ **client_block** ou **_NORMAL_BLOCK**.

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé l’opération d’allocation ou **null**.

*linenumber*<br/>
Numéro de ligne dans le fichier source où l’opération d’allocation a été demandée ou **null**.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la *mémoire tampon*. Une valeur de retour **null** indique une erreur, et **errno** a la valeur **ENOMEM**, ce qui indique que la mémoire est insuffisante pour allouer *MaxLen* octets (quand un argument **null** est fourni comme *buffer*) ou à **ERANGE** , indiquant que le chemin d’accès dépasse *MaxLen* caractères. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Les fonctions **_getdcwd_dbg** et **_wgetdcwd_dbg** sont identiques à **_getdcwd** et **_wgetdcwd** , à ceci près que, quand **_ DEBUG** est défini, ces fonctions utilisent la version de débogage de **malloc** et _ **malloc_dbg** pour Allouez de la mémoire si la **valeur null** est passée comme paramètre de *mémoire tampon* . Pour plus d’informations, consultez [_malloc_dbg](malloc-dbg.md).

Dans la plupart des cas, vous n'avez pas besoin d'appeler ces fonctions de manière explicite. Au lieu de cela, vous pouvez définir l’indicateur _ **CRTDBG_MAP_ALLOC** . Quand _ **CRTDBG_MAP_ALLOC** est défini, les appels à **_getdcwd** et **_wgetdcwd** sont remappés à **_getdcwd_dbg** et **_Wgetdcwd_dbg**, respectivement, avec le *Blocktype* défini sur **_NORMAL_BLOCK**. Vous n’avez donc pas besoin d’appeler ces fonctions de manière explicite, sauf si vous souhaitez marquer les blocs du tas comme _ **client_block**. Pour plus d’informations, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetdcwd_dbg**|**_getdcwd_dbg**|**_getdcwd_dbg**|**_wgetdcwd_dbg**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_getdcwd_dbg**|\<crtdbg.h>|
|**_wgetdcwd_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[Contrôle de répertoire](../../c-runtime-library/directory-control.md)<br/>
[Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
