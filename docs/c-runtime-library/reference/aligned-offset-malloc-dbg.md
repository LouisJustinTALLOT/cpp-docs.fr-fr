---
title: _aligned_offset_malloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_offset_malloc_dbg
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
- _aligned_offset_malloc_dbg
- aligned_offset_malloc_dbg
helpviewer_keywords:
- _aligned_offset_malloc_dbg function
- aligned_offset_malloc_dbg function
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
ms.openlocfilehash: 4fbacb170fd1ae1ce92de4a11ea85ff42b3942a0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939768"
---
# <a name="_aligned_offset_malloc_dbg"></a>_aligned_offset_malloc_dbg

Alloue de la mémoire sur une limite d’alignement spécifiée (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
void * _aligned_offset_malloc_dbg(
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Paramètres

*size*<br/>
Taille de l'allocation de mémoire demandée.

*alignment*<br/>
Valeur d'alignement, qui doit être un entier à puissance 2.

*offset*<br/>
Décalage dans l'allocation de mémoire pour forcer l'alignement.

*filename*<br/>
Pointeur vers le nom du fichier source qui a demandé l’opération d’allocation ou **null**.

*linenumber*<br/>
Numéro de ligne dans le fichier source où l’opération d’allocation a été demandée ou **null**.

## <a name="return-value"></a>Valeur de retour

Pointeur vers le bloc de mémoire qui a été alloué ou **null** en cas d’échec de l’opération.

## <a name="remarks"></a>Notes

**_aligned_offset_malloc_dbg** est une version de débogage de la fonction [_aligned_offset_malloc](aligned-offset-malloc.md) . Lorsque [_ DEBUG](../../c-runtime-library/debug.md) n’est pas défini, chaque appel à **_aligned_offset_malloc_dbg** est réduit à un appel à **_aligned_offset_malloc**. **_Aligned_offset_malloc** et **_aligned_offset_malloc_dbg** allouez un bloc de mémoire dans le tas de base, mais **_aligned_offset_malloc_dbg** offre plusieurs fonctionnalités de débogage : des mémoires tampons de chaque côté de la partie utilisateur du bloc à Testez les fuites et les informations d'*LineNumber* de *nom de fichier*/pour déterminer l’origine des demandes d’allocation. Le suivi de types d’allocation spécifiques avec un paramètre de type de bloc n’est pas une fonctionnalité de débogage prise en charge pour les allocations alignées. Les allocations alignées s’affichent sous la forme d’un type de bloc _NORMAL_BLOCK.

**_aligned_offset_malloc_dbg** alloue le bloc de mémoire avec un peu plus d’espace que la *taille*demandée. L'espace supplémentaire est utilisé par le gestionnaire de tas de débogage pour lier les blocs de mémoire de débogage et pour fournir à l'application des informations sur les en-têtes de débogage et les mémoires tampons de remplacement. Quand le bloc est alloué, la partie utilisateur du bloc est renseignée avec la valeur 0xCD et chaque mémoire tampon de remplacement est renseignée avec la valeur 0xFD.

**_aligned_offset_malloc_dbg** est utile dans les situations où l’alignement est nécessaire sur un élément imbriqué ; par exemple, si l’alignement était nécessaire sur une classe imbriquée.

**_aligned_offset_malloc_dbg** est basé sur **malloc**; Pour plus d’informations, consultez [malloc](malloc.md).

Cette fonction affecte à **errno** la valeur **ENOMEM** si l’allocation de mémoire a échoué ou si la taille demandée était supérieure à **_HEAP_MAXREQ**. Pour plus d’informations sur **errno**, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). De plus, **_aligned_offset_malloc** valide ses paramètres. Si *alignment* n’est pas une puissance de 2 ou si *offset* est supérieur ou égal à *Size* et différent de zéro, cette fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction retourne la **valeur null** et définit **errno** sur **EINVAL**.

Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version de débogage du tas de base, voir [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

Pour plus d’informations sur les types de blocs d’allocation et sur leur utilisation, consultez [Types de bloc sur le tas de débogage](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_aligned_offset_malloc_dbg**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
