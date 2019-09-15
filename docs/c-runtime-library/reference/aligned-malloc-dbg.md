---
title: _aligned_malloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_malloc_dbg
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
- _aligned_malloc_dbg
- aligned_malloc_dbg
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
ms.openlocfilehash: 3db61d494ea94c9ccbf2844c9f47df66dad87ff7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939896"
---
# <a name="_aligned_malloc_dbg"></a>_aligned_malloc_dbg

Alloue de la mémoire sur une limite d'alignement spécifiée avec de l'espace supplémentaire pour un en-tête de débogage et des mémoires tampons de remplacement (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_malloc_dbg(
    size_t size,
    size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Taille de l'allocation de mémoire demandée.

*alignment*<br/>
Valeur d'alignement, qui doit être un entier à puissance 2.

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé l'opération d'allocation ou NULL.

*linenumber*<br/>
Numéro de ligne dans le fichier source où l'opération d'allocation a été demandée ou NULL.

## <a name="return-value"></a>Valeur de retour

Pointeur vers le bloc de mémoire qui a été alloué ou NULL en cas d’échec de l’opération.

## <a name="remarks"></a>Notes

**_aligned_malloc_dbg** est une version de débogage de la fonction [_aligned_malloc](aligned-malloc.md) . Lorsque [_ DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_aligned_malloc_dbg** est réduit à un `_aligned_malloc`appel à. Et _aligned_malloc_dbg allouez un bloc de mémoire dans le tas de base, mais **_aligned_malloc_dbg** offre plusieurs fonctionnalités de débogage : des mémoires tampons de chaque côté de la partie utilisateur du bloc pour vérifier les fuites, et le nom de fichier `_aligned_malloc`informations LineNumber pour déterminer l’origine des demandes d’allocation. / Le suivi de types d’allocation spécifiques avec un paramètre de type de bloc n’est pas une fonctionnalité de débogage prise en charge pour les allocations alignées. Les allocations alignées s’affichent sous la forme d’un type de bloc _NORMAL_BLOCK.

**_aligned_malloc_dbg** alloue le bloc de mémoire avec un peu plus d’espace que la *taille*demandée. L'espace supplémentaire est utilisé par le gestionnaire de tas de débogage pour lier les blocs de mémoire de débogage et pour fournir à l'application des informations sur les en-têtes de débogage et les mémoires tampons de remplacement. Quand le bloc est alloué, la partie utilisateur du bloc est renseignée avec la valeur 0xCD et chaque mémoire tampon de remplacement est renseignée avec la valeur 0xFD.

**_aligned_malloc_dbg** affecte `errno` `_HEAP_MAXREQ`la valeur si une allocation de mémoire échoue ou si la quantité de mémoire nécessaire (y compris la surcharge mentionnée précédemment) dépasse. `ENOMEM` Pour plus d’informations sur ces codes d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). De plus, **_aligned_malloc_dbg** valide ses paramètres. Si *alignment* n’est pas une puissance de 2 ou que la *taille* est égale à zéro, cette fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne null `errno` et `EINVAL`affecte à la valeur.

Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les types de bloc d’allocation et sur leur utilisation, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur les différences entre l’appel à une fonction de tas standard et sa version de débogage dans la build de débogage d’une application, consultez [Versions Debug des fonctions d’allocation du tas](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_aligned_malloc_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)