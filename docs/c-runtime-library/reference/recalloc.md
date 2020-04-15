---
title: _recalloc
ms.date: 4/2/2020
api_name:
- _recalloc
- _o__recalloc
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: 57972a48336d8dd362b5da7513c854703134921b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338123"
---
# <a name="_recalloc"></a>_recalloc

Une combinaison de **réaffectation** et **calloc**. Réalloue un tableau en mémoire et initialise ses éléments à 0.

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

*nombre*<br/>
Nombre d'éléments.

*Taille*<br/>
Longueur en octets de chaque élément.

## <a name="return-value"></a>Valeur de retour

**_recalloc** retourne un pointeur **vide** au bloc de mémoire réaffecté (et peut-être déplacé).

S’il n’y a pas assez de mémoire disponible pour étendre le bloc à la taille donnée, le bloc d’origine est laissé inchangé, et **NULL** est retourné.

Si la taille demandée est nulle, alors le bloc pointé vers *memblock* est libéré; la valeur de retour est **NULL**, et *memblock* est laissé pointant vers un bloc libéré.

La valeur de retour pointe vers un espace de stockage qui est obligatoirement aligné correctement pour le stockage de tout type d'objet. Pour obtenir un pointeur à un type autre que **vide,** utilisez un type de fonte sur la valeur de retour.

## <a name="remarks"></a>Notes

La fonction **_recalloc** modifie la taille d’un bloc mémoire alloué. *L’argument memblock* indique le début du bloc de mémoire. Si *memblock* est **NULL**, **_recalloc** se comporte de la même manière que [calloc](calloc.md) et alloue un nouveau bloc d’octets de*taille* de *nombre.* *  Chaque élément est initialisé à 0. Si *memblock* n’est pas **NULL**, il devrait être un pointeur retourné par un appel précédent à **calloc**, [malloc](malloc.md), ou [réaffecter](realloc.md).

Parce que le nouveau bloc peut être dans un nouvel emplacement de mémoire, le pointeur retourné par **_recalloc** n’est pas garanti d’être le pointeur passé par l’argument *memblock.*

**_recalloc** définit **errno** à **ENOMEM** si l’allocation de mémoire échoue ou si la quantité de mémoire demandée dépasse **_HEAP_MAXREQ**. Pour plus d’informations sur ce code d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**recalloc** appelle **la réaffectation** afin d’utiliser la fonction [de _set_new_mode](set-new-mode.md) de Cmd pour définir le nouveau mode de manutention. Le nouveau mode de manutention indique si, en cas de défaillance, **la réaffectation** est d’appeler la nouvelle routine de gestionnaire tel qu’établi par [_set_new_handler](set-new-handler.md). Par défaut, **réaffecter** n’appelle pas la nouvelle routine de gestionnaire sur l’omission d’allouer la mémoire. Vous pouvez passer outre à ce comportement par défaut de sorte que, lorsque **_recalloc** ne parvient pas à allouer la mémoire, **réaffecter** appelle la nouvelle routine de gestionnaire de la même manière que le **nouvel** opérateur fait quand il échoue pour la même raison. Pour ce faire, appelez

```C
_set_new_mode(1);
```

au début de votre programme, ou créez un lien avec NEWMODE.OBJ.

Lorsque l’application est liée à une version débogé de déboguer des bibliothèques C run-time, **_recalloc** se résout à [_recalloc_dbg](recalloc-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**_recalloc** est marquée `__declspec(noalias)` `__declspec(restrict)`et, ce qui signifie que la fonction est garantie de ne pas modifier les variables globales, et que le pointeur retourné n’est pas alias. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md) et [restrict](../../cpp/restrict.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

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
[Gratuit](free.md)<br/>
[Options de lien](../../c-runtime-library/link-options.md)<br/>
