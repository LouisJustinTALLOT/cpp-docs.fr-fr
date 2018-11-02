---
title: _recalloc
ms.date: 11/04/2016
apiname:
- _recalloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: 3bcc238dcb950a8e30af16efc557e99d933efe92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436515"
---
# <a name="recalloc"></a>_recalloc

Une combinaison de **realloc** et **calloc**. Réalloue un tableau en mémoire et initialise ses éléments à 0.

## <a name="syntax"></a>Syntaxe

```C
void *_recalloc(
   void *memblock
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>Paramètres

*memblock*<br/>
Pointeur désignant le bloc de mémoire précédemment alloué.

*Nombre*<br/>
Nombre d'éléments.

*size*<br/>
Longueur en octets de chaque élément.

## <a name="return-value"></a>Valeur de retour

**_recalloc** retourne un **void** pointeur vers le bloc de mémoire réalloué (et éventuellement déplacé).

Si vous ne comporte pas suffisamment de mémoire disponible pour étendre le bloc à la taille donnée, le bloc d’origine reste inchangé, et **NULL** est retourné.

Si la taille demandée est zéro, le bloc désigné par *memblock* est libéré ; la valeur de retour est **NULL**, et *memblock* pointe vers un bloc libéré.

La valeur de retour pointe vers un espace de stockage qui est obligatoirement aligné correctement pour le stockage de tout type d'objet. Pour obtenir un pointeur vers un type autre que **void**, utilisez un cast de type sur la valeur de retour.

## <a name="remarks"></a>Notes

Le **_recalloc** fonction modifie la taille d’un bloc de mémoire alloué. Le *memblock* argument pointe vers le début du bloc de mémoire. Si *memblock* est **NULL**, **_recalloc** se comporte de la même façon que [calloc](calloc.md) et alloue un nouveau bloc de *nombre*  *  *taille* octets. Chaque élément est initialisé à 0. Si *memblock* n’est pas **NULL**, il doit être un pointeur retourné par un appel précédent à **calloc**, [malloc](malloc.md), ou [realloc ](realloc.md).

Étant donné que le nouveau bloc peut être dans un nouvel emplacement de mémoire, le pointeur retourné par **_recalloc** n’est pas garanti pour être le pointeur transmis via le *memblock* argument.

**_recalloc** définit **errno** à **ENOMEM** si l’allocation de mémoire échoue ou si la quantité de mémoire demandée dépasse **_HEAP_MAXREQ**. Pour plus d’informations sur ce code d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**recalloc** appels **realloc** pour pouvoir utiliser le C++ [_set_new_mode](set-new-mode.md) fonction permettant de définir le mode de nouveau gestionnaire. Le nouveau mode de gestionnaire indique si, en cas d’échec, **realloc** consiste à appeler la routine de nouveau gestionnaire telle que définie par [_set_new_handler](set-new-handler.md). Par défaut, **realloc** n’appelle pas la routine de nouveau gestionnaire en cas d’échec d’allocation de mémoire. Vous pouvez remplacer ce comportement par défaut afin que, lorsque **_recalloc** ne parvient pas à allouer de la mémoire, **realloc** appelle la routine de nouveau gestionnaire de la même façon que le **nouveau** opérateur fait en cas d’échec pour la même raison. Pour remplacer la valeur par défaut, appelez

```C
_set_new_mode(1);
```

au début de votre programme, ou créez un lien avec NEWMODE.OBJ.

Lorsque l’application est liée à une version debug des bibliothèques Runtime C, **_recalloc** se résout en [_recalloc_dbg](recalloc-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**_recalloc** est marquée `__declspec(noalias)` et `__declspec(restrict)`, ce qui signifie que la fonction ne peut ne pas modifier les variables globales et que le pointeur retourné n’est pas un alias. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md) et [restrict](../../cpp/restrict.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> et \<malloc.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[free](free.md)<br/>
[Options de lien](../../c-runtime-library/link-options.md)<br/>
