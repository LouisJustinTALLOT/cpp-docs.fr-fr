---
title: _malloc_dbg
ms.date: 11/04/2016
api_name:
- _malloc_dbg
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
- malloc_dbg
- _malloc_dbg
helpviewer_keywords:
- malloc_dbg function
- memory allocation
- _malloc_dbg function
ms.assetid: c97eca51-140b-4461-8bd2-28965b49ecdb
ms.openlocfilehash: cfaaaec17dc8546c937045f93027e9609981bd93
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952877"
---
# <a name="_malloc_dbg"></a>_malloc_dbg

Alloue un bloc de mémoire dans le tas avec de l'espace supplémentaire pour un en-tête de débogage et des mémoires tampons de remplacement (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void *_malloc_dbg(
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Taille demandée du bloc de mémoire (en octets).

*blockType*<br/>
Type demandé du bloc de mémoire : _ **client_block** ou **_NORMAL_BLOCK**.

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé l’opération d’allocation ou **null**.

*linenumber*<br/>
Numéro de ligne dans le fichier source où l’opération d’allocation a été demandée ou **null**.

Les paramètres *filename* et *LineNumber* ne sont disponibles que si _ **malloc_dbg** a été appelé explicitement ou si la constante de préprocesseur _ [CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) a été définie.

## <a name="return-value"></a>Valeur de retour

Une fois l’opération réussie, cette fonction retourne un pointeur vers la partie utilisateur du bloc de mémoire alloué, appelle la nouvelle fonction de gestionnaire ou retourne la **valeur null**. Pour obtenir une description complète du comportement de retour, voir la section Notes suivante. Pour plus d’informations sur l’utilisation de la fonction du nouveau gestionnaire, consultez la fonction [malloc](malloc.md).

## <a name="remarks"></a>Notes

_ **malloc_dbg** est une version de débogage de la fonction [malloc](malloc.md) . Lorsque [_ DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à _ **malloc_dbg** est réduit à un appel à **malloc**. **Malloc** et _ **malloc_dbg** allouent tous deux un bloc de mémoire dans le tas de base, mais _ **malloc_dbg** offre plusieurs fonctionnalités de débogage : des mémoires tampons de chaque côté de la partie utilisateur du bloc pour tester les fuites, un paramètre de type de bloc à suivre des types d’allocation spécifiques et des informations de *nom de fichier*/*LineNumber* pour déterminer l’origine des demandes d’allocation.

_ **malloc_dbg** alloue le bloc de mémoire avec un peu plus d’espace que la *taille*demandée. L'espace supplémentaire est utilisé par le gestionnaire de tas de débogage pour lier les blocs de mémoire de débogage et pour fournir à l'application des informations sur les en-têtes de débogage et les mémoires tampons de remplacement. Quand le bloc est alloué, la partie utilisateur du bloc est renseignée avec la valeur 0xCD et chaque mémoire tampon de remplacement est renseignée avec la valeur 0xFD.

_ **malloc_dbg** affecte à **errno** la valeur **ENOMEM** si l’allocation de mémoire échoue ou si la quantité de mémoire nécessaire (y compris la surcharge mentionnée précédemment) dépasse **_HEAP_MAXREQ**. Pour plus d’informations sur ces codes d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les types de bloc d’allocation et sur leur utilisation, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les différences entre l’appel à une fonction de tas standard et sa version de débogage dans la build de débogage d’une application, consultez [Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_malloc_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de _ **malloc_dbg**, consultez [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
[malloc](malloc.md)<br/>
[_calloc_dbg](calloc-dbg.md)<br/>
