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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 45f483bcaa397969a81097768ebbd1ed4cda288b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226188"
---
# <a name="_recalloc"></a>_recalloc

Combinaison de **realloc** et de **calloc**. Réalloue un tableau en mémoire et initialise ses éléments à 0.

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

*number*<br/>
Nombre d'éléments.

*size*<br/>
Longueur en octets de chaque élément.

## <a name="return-value"></a>Valeur de retour

**_recalloc** retourne un **`void`** pointeur vers le bloc de mémoire réalloué (et éventuellement déplacé).

Si la mémoire disponible est insuffisante pour étendre le bloc à la taille donnée, le bloc d’origine reste inchangé et la **valeur null** est retournée.

Si la taille demandée est égale à zéro, le bloc pointé par *memblock* est libéré ; la valeur de retour est **null**et *memblock* pointe vers un bloc libéré.

La valeur de retour pointe vers un espace de stockage qui est obligatoirement aligné correctement pour le stockage de tout type d'objet. Pour obtenir un pointeur vers un type autre que **`void`** , utilisez un cast de type sur la valeur de retour.

## <a name="remarks"></a>Notes

La fonction **_recalloc** modifie la taille d’un bloc de mémoire alloué. L’argument *memblock* pointe vers le début du bloc de mémoire. Si *memblock* a **la valeur null**, **_recalloc** se comporte de la même façon que [calloc](calloc.md) et alloue un nouveau bloc de *nombre*d’octets de  *  *taille* . Chaque élément est initialisé à 0. Si *memblock* n’a pas la **valeur null**, il doit s’agir d’un pointeur retourné par un appel précédent à **calloc**, [malloc](malloc.md)ou [realloc](realloc.md).

Étant donné que le nouveau bloc peut se trouver dans un nouvel emplacement de mémoire, il n’est pas garanti que le pointeur renvoyé par **_recalloc** soit le pointeur transmis via l’argument *memblock* .

**_recalloc** affecte à **errno** la valeur **ENOMEM** si l’allocation de mémoire échoue ou si la quantité de mémoire demandée dépasse **_HEAP_MAXREQ**. Pour plus d’informations sur ce code d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**recalloc** appelle **realloc** afin d’utiliser la fonction de [_set_new_mode](set-new-mode.md) C++ pour définir le nouveau mode de gestionnaire. Le nouveau mode de gestionnaire indique si, en cas d’échec, **realloc** est appelé à appeler la routine de nouveau gestionnaire telle qu’elle est définie par [_set_new_handler](set-new-handler.md). Par défaut, **realloc** n’appelle pas la routine de nouveau gestionnaire en cas d’échec d’allocation de mémoire. Vous pouvez remplacer ce comportement par défaut afin que, lorsque **_recalloc** ne parvient pas à allouer de la mémoire, **réalloue appelle la** routine de nouveau gestionnaire de la même façon que l' **`new`** opérateur quand il échoue pour la même raison. Pour ce faire, appelez

```C
_set_new_mode(1);
```

au début de votre programme, ou créez un lien avec NEWMODE.OBJ.

Lorsque l’application est liée à une version Debug des bibliothèques Runtime C, **_recalloc** se résout en [_recalloc_dbg](recalloc-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**_recalloc** est marqué `__declspec(noalias)` et `__declspec(restrict)` , ce qui signifie que la fonction est garantie de ne pas modifier les variables globales et que le pointeur retourné n’a pas d’alias. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md) et [restrict](../../cpp/restrict.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

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
