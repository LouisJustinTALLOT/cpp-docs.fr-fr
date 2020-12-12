---
description: 'En savoir plus sur : _realloc_dbg'
title: _realloc_dbg
ms.date: 11/04/2016
api_name:
- _realloc_dbg
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
- _realloc_dbg
- realloc_dbg
helpviewer_keywords:
- reallocating memory blocks
- realloc_dbg function
- memory blocks, reallocating
- memory, reallocating
- _realloc_dbg function
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
ms.openlocfilehash: 1a211ac886de34d6b251622dec2f4500bb290d14
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274786"
---
# <a name="_realloc_dbg"></a>_realloc_dbg

Réalloue un bloc de mémoire spécifié dans le tas en déplaçant et/ou redimensionnant le bloc (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void *_realloc_dbg(
   void *userData,
   size_t newSize,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Paramètres

*Permanence*<br/>
Pointeur vers le bloc de mémoire précédemment alloué.

*newSize*<br/>
Taille demandée pour le bloc réalloué (octets).

*blockType*<br/>
Type demandé pour le bloc réalloué : **_CLIENT_BLOCK** ou **_NORMAL_BLOCK**.

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé l’opération de **réallocation** ou **null**.

*LineNumber*<br/>
Numéro de ligne dans le fichier source où l’opération de **réallocation** a été demandée ou **null**.

Les paramètres *filename* et *LineNumber* ne sont disponibles que si **_realloc_dbg** a été appelé explicitement ou si la constante de préprocesseur [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) a été définie.

## <a name="return-value"></a>Valeur renvoyée

Une fois l’opération réussie, cette fonction retourne un pointeur vers la partie utilisateur du bloc de mémoire réalloué, appelle la nouvelle fonction de gestionnaire ou retourne la **valeur null**. Pour obtenir une description complète du comportement de retour, voir la section Notes suivante. Pour plus d’informations sur l’utilisation de la fonction de nouveau gestionnaire, voir la fonction [realloc](realloc.md).

## <a name="remarks"></a>Notes

**_realloc_dbg** est une version de débogage de la fonction [realloc](realloc.md) . Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_realloc_dbg** est réduit à un appel à **realloc**. **Realloc** et **_realloc_dbg** réallouent un bloc de mémoire dans le tas de base, mais **_realloc_dbg** prend en charge plusieurs fonctionnalités de débogage : des mémoires tampons de chaque côté de la partie utilisateur du bloc pour tester les fuites, un paramètre de type de bloc pour suivre des types d’allocation spécifiques et des informations de nom de *fichier* / *LineNumber* pour déterminer l’origine des demandes d’allocation.

**_realloc_dbg** réalloue le bloc de mémoire spécifié avec un peu plus d’espace que la fonction *NewSize* demandée. *NewSize* peut être supérieure ou inférieure à la taille du bloc de mémoire alloué initialement. L'espace supplémentaire est utilisé par le gestionnaire de tas de débogage pour lier les blocs de mémoire de débogage et pour fournir à l'application des informations sur les en-têtes de débogage et les mémoires tampons de remplacement. La réallocation peut entraîner un déplacement du bloc de mémoire initial vers un autre emplacement dans le tas, ainsi qu'une modification de la taille du bloc de mémoire. Si le bloc de mémoire est déplacé, son contenu d'origine est remplacé.

**_realloc_dbg** affecte à **errno** la valeur **ENOMEM** si l’allocation de mémoire échoue ou si la quantité de mémoire nécessaire (y compris la surcharge mentionnée précédemment) dépasse **_HEAP_MAXREQ**. Pour obtenir des informations sur ce code de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les types de blocs d’allocation et sur leur utilisation, consultez [types de blocs sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les différences entre l’appel à une fonction de tas standard et sa version de débogage dans la build de débogage d’une application, consultez [Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_realloc_dbg**|\<crtdbg.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Consultez l’exemple présenté dans la rubrique [_msize_dbg](msize-dbg.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
