---
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: eefbe957ce5057b5038f98bc8da8fb2f0bdd3d1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345980"
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

La fonction **libre** traite un bloc de mémoire (*memblock*) qui a été précédemment alloué par un appel à **calloc**, **malloc**, ou **réaffecter**. Le nombre d’octets libérés est équivalent au nombre d’octets demandés lors de l’attribution du bloc (ou réaffecté, dans le cas **d’une réaffectation).** Si *memblock* est **NULL**, le pointeur est ignoré et **gratuit** revient immédiatement. Tenter de libérer un pointeur invalide (un pointeur à un bloc de mémoire qui n’a pas été alloué par **calloc**, **malloc**, ou **réaffecter**) peut affecter les demandes d’allocation ultérieures et causer des erreurs.

Si une erreur se produit en libérant la mémoire, **errno** est réglé avec des informations du système d’exploitation sur la nature de l’échec. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Une fois qu’un bloc de mémoire a été libéré, [_heapmin](heapmin.md) réduit la quantité de mémoire disponible sur le tas en fusionnant les régions inutilisées et en les libérant pour le système d’exploitation. La mémoire libérée qui n’est pas mise à la disposition du système d’exploitation est restaurée vers le pool libre et peut être réallouée.

Lorsque l’application est liée à une version débogé de déboçons des bibliothèques C run-time, **la solution gratuite** à [_free_dbg](free-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**libre** est `__declspec(noalias)`marqué, ce qui signifie que la fonction est garantie de ne pas modifier les variables globales. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md).

Pour libérer de la mémoire allouée avec [_malloca](malloca.md), utilisez [_freea](freea.md).

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**Gratuit**|\<stdlib.h> et \<malloc.h>|

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
