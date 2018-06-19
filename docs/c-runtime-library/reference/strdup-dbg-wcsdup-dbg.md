---
title: _strdup_dbg, _wcsdup_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _strdup_dbg
- _wcsdup_dbg
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
- _wcsdup_dbg
- strdup_dbg
- _strdup_dbg
- wcsdup_dbg
dev_langs:
- C++
helpviewer_keywords:
- _wcsdup_dbg function
- stdup_dbg function
- copying strings
- duplicating strings
- strings [C++], copying
- strings [C++], duplicating
- _strdup_dbg function
- wcsdup_dbg function
ms.assetid: 681db70c-d124-43ab-b83e-5eeea9035097
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b6e8f5f4634ec93cab619c1e073fa8071691fe6
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451378"
---
# <a name="strdupdbg-wcsdupdbg"></a>_strdup_dbg, _wcsdup_dbg

Les versions de [_strdup et _wcsdup](strdup-wcsdup-mbsdup.md) qui utilisent la version debug de **malloc**.

## <a name="syntax"></a>Syntaxe

```C
char *_strdup_dbg(
   const char *strSource,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wcsdup_dbg(
   const wchar_t *strSource,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Paramètres

*strSource*<br/>
Chaîne source se terminant par null.

*blockType*<br/>
Type de bloc de mémoire demandé : **_CLIENT_BLOCK** ou **_NORMAL_BLOCK**.

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé l’opération d’allocation ou **NULL**.

*linenumber*<br/>
Numéro de ligne dans le fichier source où l’opération d’allocation a été demandée ou **NULL**.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur vers l’emplacement de stockage de la chaîne copiée ou **NULL** si le stockage ne peut pas être alloué.

## <a name="remarks"></a>Notes

Le **_strdup_dbg** et **_wcsdup_dbg** fonctions sont identiques aux **_strdup** et **_wcsdup** , sauf que, lorsque **_ DÉBOGUER** est défini, ces fonctions utilisent la version debug de **malloc**, **_malloc_dbg**, allocation de mémoire pour la chaîne dupliquée. Pour plus d’informations sur les fonctionnalités de débogage de **_malloc_dbg**, consultez [_malloc_dbg](malloc-dbg.md).

Dans la plupart des cas, vous n'avez pas besoin d'appeler ces fonctions de manière explicite. Au lieu de cela, vous pouvez définir l’indicateur **_CRTDBG_MAP_ALLOC**. Lorsque **_CRTDBG_MAP_ALLOC** est défini, les appels à **_strdup** et **_wcsdup** sont remappés à **_strdup_dbg** et **_ wcsdup_dbg**, respectivement, avec la *blockType* la valeur **_NORMAL_BLOCK**. Par conséquent, il est inutile d’appeler ces fonctions de manière explicite sauf si vous souhaitez marquer les blocs du tas comme **_CLIENT_BLOCK**. Pour plus d’informations sur les types de bloc, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsdup_dbg**|**_strdup_dbg**|**_mbsdup**|**_wcsdup_dbg**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_strdup_dbg**, **_wcsdup_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions debug des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdup, _wcsdup, _mbsdup](strdup-wcsdup-mbsdup.md)<br/>
[Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
