---
description: 'En savoir plus sur : _recalloc_dbg'
title: _recalloc_dbg
ms.date: 11/04/2016
api_name:
- _recalloc_dbg
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
- recalloc_dbg
- _recalloc_dbg
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
ms.openlocfilehash: abad8ff877a78bc589a48da689766322ad8438de
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254259"
---
# <a name="_recalloc_dbg"></a>_recalloc_dbg

Réalloue un tableau et initialise ses éléments à 0 (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void *_recalloc_dbg(
   void *userData,
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Paramètres

*Permanence*<br/>
Pointeur vers le bloc de mémoire précédemment alloué.

*number*<br/>
Nombre de blocs de mémoire demandé.

*size*<br/>
Taille de chaque bloc de mémoire demandée (octets).

*blockType*<br/>
Type de bloc de mémoire demandé : **_CLIENT_BLOCK** ou **_NORMAL_BLOCK**.

Pour plus d’informations sur les types de blocs d’allocation et sur leur utilisation, consultez [types de blocs sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details).

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé l’opération d’allocation ou **null**.

*LineNumber*<br/>
Numéro de ligne dans le fichier source où l’opération d’allocation a été demandée ou **null**.

Les paramètres *filename* et *LineNumber* ne sont disponibles que si **_recalloc_dbg** a été appelé explicitement ou si la constante de préprocesseur [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) a été définie.

## <a name="return-value"></a>Valeur renvoyée

Une fois l’opération réussie, cette fonction retourne un pointeur vers la partie utilisateur du bloc de mémoire réalloué, appelle la nouvelle fonction de gestionnaire ou retourne la **valeur null**. Pour obtenir une description complète du comportement de retour, voir la section Notes suivante. Pour plus d’informations sur l’utilisation de la fonction de nouveau gestionnaire, voir la fonction [_malloc](recalloc.md).

## <a name="remarks"></a>Notes

**_recalloc_dbg** est une version de débogage de la fonction [_recalloc](recalloc.md) . Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_recalloc_dbg** est réduit à un appel à **_recalloc**. **_Recalloc** et **_recalloc_dbg** réallouent un bloc de mémoire dans le tas de base, mais **_recalloc_dbg** prend en charge plusieurs fonctionnalités de débogage : des mémoires tampons de chaque côté de la partie utilisateur du bloc pour tester les fuites, un paramètre de type de bloc pour effectuer le suivi de types d’allocation spécifiques et des informations de *nom de fichier* / *LineNumber* pour déterminer l’origine des demandes d’allocation.

**_recalloc_dbg** réalloue le bloc de mémoire spécifié avec un peu plus d’espace que lataille demandée (  *  *taille* de nombre), qui peut être supérieure ou inférieure à la taille du bloc de mémoire alloué initialement. L'espace supplémentaire est utilisé par le gestionnaire de tas de débogage pour lier les blocs de mémoire de débogage et pour fournir à l'application des informations sur les en-têtes de débogage et les mémoires tampons de remplacement. La réallocation peut entraîner un déplacement du bloc de mémoire initial vers un autre emplacement dans le tas, ainsi qu'une modification de la taille du bloc de mémoire. La partie utilisateur du bloc contient la valeur 0xCD et chaque mémoire tampon de remplacement contient 0xFD.

**_recalloc_dbg** affecte à **errno** la valeur **ENOMEM** si une allocation de mémoire échoue ; **EINVAL** est retourné si la quantité de mémoire nécessaire (y compris la surcharge mentionnée précédemment) dépasse **_HEAP_MAXREQ**. Pour obtenir des informations sur ce code de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les différences entre l’appel à une fonction de tas standard et sa version de débogage dans la build de débogage d’une application, consultez [Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_recalloc_dbg**|\<crtdbg.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
