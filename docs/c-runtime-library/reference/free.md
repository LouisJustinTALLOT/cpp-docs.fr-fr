---
title: free | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- free
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
- free
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35a1ae1a27b08db14673b125ecbc2978fd4738a3
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100481"
---
# <a name="free"></a>free

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

Le **gratuit** fonction libère un bloc de mémoire (*memblock*) qui a été précédemment alloué par un appel à **calloc**, **malloc**, ou **realloc**. Le nombre d’octets libérés est équivalent au nombre d’octets demandés quand le bloc a été alloué (ou réalloué, dans le cas de **realloc**). Si *memblock* est **NULL**, le pointeur est ignoré et **gratuit** retourne immédiatement. Tenter de libérer un pointeur non valide (un pointeur désignant un bloc de mémoire qui n’était pas alloué par **calloc**, **malloc**, ou **realloc**) peut affecter les demandes d’allocation ultérieures et provoquer des erreurs.

Si une erreur se produit pendant la libération de la mémoire, **errno** est définie avec des informations sur la nature de la défaillance du système d’exploitation. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Une fois qu’un bloc de mémoire a été libéré, [_heapmin](heapmin.md) réduit la quantité de mémoire disponible sur le tas en fusionnant les régions inutilisées et en les libérant pour le système d’exploitation. La mémoire libérée qui n’est pas mise à la disposition du système d’exploitation est restaurée vers le pool libre et peut être réallouée.

Lorsque l’application est liée à une version debug des bibliothèques Runtime C, **gratuit** se résout en [_free_dbg](free-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**gratuit** est marqué `__declspec(noalias)`, ce qui signifie que la fonction ne peut ne pas modifier les variables globales. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md).

Pour libérer de la mémoire allouée avec [_malloca](malloca.md), utilisez [_freea](freea.md).

## <a name="requirements"></a>Configuration requise

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
