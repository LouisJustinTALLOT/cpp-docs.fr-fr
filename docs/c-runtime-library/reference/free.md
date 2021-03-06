---
description: 'En savoir plus sur : gratuit'
title: gratuit
ms.date: 4/2/2020
api_name:
- free
- _o_free
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
- free
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
ms.openlocfilehash: 731bd1ea6cf3bfe56bf71ee762fb3477346ddf13
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314020"
---
# <a name="free"></a>gratuit

Libère un bloc de mémoire.

## <a name="syntax"></a>Syntaxe

```C
void free(
   void *memblock
);
```

### <a name="parameters"></a>Paramètres

*memblock*<br/>
Bloc mémoire précédemment alloué à libérer.

## <a name="remarks"></a>Notes

La fonction **Free libère** un bloc de mémoire (*memblock*) qui a été précédemment alloué par un appel à **calloc**, **malloc** ou **realloc**. Le nombre d’octets libérés est équivalent au nombre d’octets demandés quand le bloc a été alloué (ou réalloué, dans le cas de **realloc**). Si *memblock* a la **valeur null**, le pointeur est ignoré et la fonction **Free** retourne immédiatement la valeur. Toute tentative de libération d’un pointeur non valide (un pointeur vers un bloc de mémoire qui n’a pas été alloué par **calloc**, **malloc** ou **realloc**) peut affecter les demandes d’allocation ultérieures et provoquer des erreurs.

Si une erreur se produit lors de la libération de la mémoire, **errno** est défini avec les informations du système d’exploitation sur la nature de la défaillance. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Une fois qu’un bloc de mémoire a été libéré, [_heapmin](heapmin.md) réduit la quantité de mémoire disponible sur le tas en fusionnant les régions inutilisées et en les libérant pour le système d’exploitation. La mémoire libérée qui n’est pas mise à la disposition du système d’exploitation est restaurée vers le pool libre et peut être réallouée.

Lorsque l’application est liée à une version de débogage des bibliothèques Runtime C, la résolution **gratuite** est résolue en [_free_dbg](free-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**Free** est marqué `__declspec(noalias)` , ce qui signifie que la fonction ne peut pas modifier les variables globales. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md).

Pour libérer de la mémoire allouée avec [_malloca](malloca.md), utilisez [_freea](freea.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**free**|\<stdlib.h> et \<malloc.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [malloc](malloc.md).

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[_alloca](alloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
[_freea](freea.md)<br/>
