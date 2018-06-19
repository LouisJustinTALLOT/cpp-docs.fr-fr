---
title: _fullpath_dbg, _wfullpath_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wfullpath_dbg
- _fullpath_dbg
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
- wfullpath_dbg
- _wfullpath_dbg
- _fullpath_dbg
- fullpath_dbg
dev_langs:
- C++
helpviewer_keywords:
- _fullpath_dbg function
- relative file paths
- absolute paths
- fullpath_dbg function
- _wfullpath_dbg function
- wfullpath_dbg function
ms.assetid: 81f72f85-07da-4f5c-866a-598e0fb03f6b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d04f3d7b53eca27d38a38b0bce284c17b15cae02
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450893"
---
# <a name="fullpathdbg-wfullpathdbg"></a>_fullpath_dbg, _wfullpath_dbg

Les versions de [_fullpath, _wfullpath](fullpath-wfullpath.md) qui utilisent la version debug de **malloc** pour allouer de la mémoire.

## <a name="syntax"></a>Syntaxe

```C
char *_fullpath_dbg(
   char *absPath,
   const char *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wfullpath_dbg(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Paramètres

*absPath*<br/>
Pointeur vers une mémoire tampon contenant le nom de chemin d’accès absolu ou complet, ou **NULL**.

*relPath*<br/>
Nom de chemin d’accès relatif.

*maxLength*<br/>
Longueur maximale du tampon du nom de chemin d’accès absolu (*absPath*). Cette longueur est exprimée en octets pour **_fullpath** mais en caractères larges (**wchar_t**) pour **_wfullpath**.

*blockType*<br/>
Type de bloc de mémoire demandé : **_CLIENT_BLOCK** ou **_NORMAL_BLOCK**.

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé l’opération d’allocation ou **NULL**.

*linenumber*<br/>
Numéro de ligne dans le fichier source où l’opération d’allocation a été demandée ou **NULL**.

## <a name="return-value"></a>Valeur de retour

Chaque fonction retourne un pointeur vers une mémoire tampon contenant le nom de chemin d’accès absolu (*absPath*). S’il existe une erreur (par exemple, si la valeur passée dans *relPath* comprend une lettre de lecteur qui n’est pas valide ou est introuvable, ou si la longueur du nom de chemin d’accès absolu créé (*absPath*) est supérieur à *maxLength*) la fonction retourne **NULL**.

## <a name="remarks"></a>Notes

Le **_fullpath_dbg** et **_wfullpath_dbg** fonctions sont identiques aux **_fullpath** et **_wfullpath** , sauf que, lorsque **_DEBUG** est défini, ces fonctions utilisent la version debug de **malloc**, **_malloc_dbg**, allocation de mémoire si **NULL** est passé en tant que premier paramètre. Pour plus d’informations sur les fonctionnalités de débogage de **_malloc_dbg**, consultez [_malloc_dbg](malloc-dbg.md).

Dans la plupart des cas, vous n'avez pas besoin d'appeler ces fonctions de manière explicite. Au lieu de cela, vous pouvez définir le **_CRTDBG_MAP_ALLOC** indicateur. Lorsque **_CRTDBG_MAP_ALLOC** est défini, les appels à **_fullpath** et **_wfullpath** sont remappés à **_fullpath_dbg** et **_wfullpath_dbg**, respectivement, avec la *blockType* la valeur **_NORMAL_BLOCK**. Par conséquent, il est inutile d’appeler ces fonctions de manière explicite sauf si vous souhaitez marquer les blocs du tas comme **_CLIENT_BLOCK**. Pour plus d’informations, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath_dbg**|**_fullpath_dbg**|**_fullpath_dbg**|**_wfullpath_dbg**|

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fullpath_dbg**|\<crtdbg.h>|
|**_wfullpath_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
