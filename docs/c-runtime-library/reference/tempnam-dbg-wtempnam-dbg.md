---
title: _tempnam_dbg, _wtempnam_dbg
ms.date: 11/04/2016
api_name:
- _wtempnam_dbg
- _tempnam_dbg
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
- wtempnam_dbg
- tempnam_dbg
- _tempnam_dbg
- _wtempnam_dbg
helpviewer_keywords:
- file names [C++], creating temporary
- tempnam_dbg function
- temporary files, creating
- file names [C++], temporary
- wtempnam_dbg function
- _tempnam_dbg function
- _wtempnam_dbg function
ms.assetid: e3760bb4-bb01-4808-b689-2c45af56a170
ms.openlocfilehash: 73642730995ac5c0b47519fac64b30400d47767c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946253"
---
# <a name="_tempnam_dbg-_wtempnam_dbg"></a>_tempnam_dbg, _wtempnam_dbg

Les versions de fonction de [_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) qui utilisent la version Debug de **malloc**, _ **malloc_dbg**.

## <a name="syntax"></a>Syntaxe

```C
char *_tempnam_dbg(
   const char *dir,
   const char *prefix,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wtempnam_dbg(
   const wchar_t *dir,
   const wchar_t *prefix,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Paramètres

*dir*<br/>
Chemin d’accès utilisé dans le nom de fichier en l’absence de variable d’environnement TMP ou si TMP n’est pas un répertoire valide.

*prefix*<br/>
Chaîne qui sera précédée des noms retournés par **_tempnam**.

*blockType*<br/>
Type de bloc de mémoire demandé : _ **client_block** ou **_NORMAL_BLOCK**.

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé l’opération d’allocation ou **null**.

*linenumber*<br/>
Numéro de ligne dans le fichier source où l’opération d’allocation a été demandée ou **null**.

## <a name="return-value"></a>Valeur de retour

Chaque fonction retourne un pointeur vers le nom généré ou **null** en cas d’échec. Une défaillance peut se produire si un nom de répertoire non valide est spécifié dans la variable d’environnement TMP et dans le paramètre *dir* .

> [!NOTE]
> **gratuit** (ou **free_dbg**) doit être appelé pour les pointeurs alloués par **_tempnam_dbg** et **_wtempnam_dbg**.

## <a name="remarks"></a>Notes

Les fonctions **_tempnam_dbg** et **_wtempnam_dbg** sont identiques à **_tempnam** et **_wtempnam** , à ceci près que, quand **_ DEBUG** est défini, ces fonctions utilisent la version Debug de **malloc** et _ **malloc_dbg**, pour Allouez de la mémoire si la **valeur null** est passée comme premier paramètre. Pour plus d’informations, consultez [_malloc_dbg](malloc-dbg.md).

Dans la plupart des cas, vous n'avez pas besoin d'appeler ces fonctions de manière explicite. Au lieu de cela, vous pouvez définir l’indicateur _ **CRTDBG_MAP_ALLOC**. Quand _ **CRTDBG_MAP_ALLOC** est défini, les appels à **_tempnam** et **_wtempnam** sont remappés à **_tempnam_dbg** et **_Wtempnam_dbg**, respectivement, avec le *Blocktype* défini sur **_NORMAL_BLOCK**. Vous n’avez donc pas besoin d’appeler ces fonctions de manière explicite, sauf si vous souhaitez marquer les blocs du tas comme _ **client_block**. Pour plus d’informations, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttempnam_dbg**|**_tempnam_dbg**|**_tempnam_dbg**|**_wtempnam_dbg**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_tempnam_dbg**, **_wtempnam_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
