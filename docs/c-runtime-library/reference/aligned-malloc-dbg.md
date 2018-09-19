---
title: _aligned_malloc_dbg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _aligned_malloc_dbg
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
- _aligned_malloc_dbg
- aligned_malloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 076ccfcf164eb17e2a855f175c8714cd63a91817
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093041"
---
# <a name="alignedmallocdbg"></a>_aligned_malloc_dbg

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

*Alignement*<br/>
Valeur d'alignement, qui doit être un entier à puissance 2.

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé l'opération d'allocation ou NULL.

*linenumber*<br/>
Numéro de ligne dans le fichier source où l'opération d'allocation a été demandée ou NULL.

## <a name="return-value"></a>Valeur de retour

Un pointeur vers le bloc de mémoire qui a été alloué ou NULL si l’opération a échoué.

## <a name="remarks"></a>Notes

**_aligned_malloc_dbg** est une version debug de la [_aligned_malloc](aligned-malloc.md) (fonction). Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_aligned_malloc_dbg** est réduite à un appel à `_aligned_malloc`. Les deux `_aligned_malloc` et **_aligned_malloc_dbg** allouer un bloc de mémoire dans le tas de base, mais **_aligned_malloc_dbg** propose plusieurs fonctionnalités de débogage : mémoires tampons de chaque côté de la partie de l’utilisateur de la bloc pour vérifier la présence de fuites, et *filename*/*linenumber* informations pour déterminer l’origine des demandes d’allocation.

**_aligned_malloc_dbg** alloue le bloc de mémoire avec un peu plus d’espace que demandé *taille*. L'espace supplémentaire est utilisé par le gestionnaire de tas de débogage pour lier les blocs de mémoire de débogage et pour fournir à l'application des informations sur les en-têtes de débogage et les mémoires tampons de remplacement. Quand le bloc est alloué, la partie utilisateur du bloc est renseignée avec la valeur 0xCD et chaque mémoire tampon de remplacement est renseignée avec la valeur 0xFD.

**_aligned_malloc_dbg** définit `errno` à `ENOMEM` si une allocation de mémoire échoue ou si la quantité de mémoire nécessaire (y compris la surcharge mentionnée précédemment) dépasse `_HEAP_MAXREQ`. Pour plus d’informations sur ces codes d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). En outre, **_aligned_malloc_dbg** valide ses paramètres. Si *alignement* n’est pas une puissance de 2 ou *taille* est égal à zéro, cette fonction appelle le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne NULL et affecte `errno` à `EINVAL`.

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