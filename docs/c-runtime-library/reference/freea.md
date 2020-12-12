---
description: 'En savoir plus sur : _freea'
title: _freea
ms.date: 11/04/2016
api_name:
- _freea
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
- freea
- _freea
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
ms.openlocfilehash: 6d6f57117265e62e7d3c822110b52f69cb65ffac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282963"
---
# <a name="_freea"></a>_freea

Libère un bloc de mémoire.

## <a name="syntax"></a>Syntaxe

```C
void _freea(
   void *memblock
);
```

### <a name="parameters"></a>Paramètres

*memblock*<br/>
Bloc mémoire précédemment alloué à libérer.

## <a name="return-value"></a>Valeur renvoyée

Aucun.

## <a name="remarks"></a>Notes

La fonction **_freea** libère un bloc de mémoire (*memblock*) précédemment alloué par un appel à [_malloca](malloca.md). **_freea** vérifie si la mémoire a été allouée sur le tas ou la pile. S’il a été alloué sur la pile, **_freea** ne fait rien. Si elle a été allouée sur le tas, le nombre d’octets libérés est équivalent au nombre d’octets demandés quand le bloc a été alloué. Si *memblock* a la **valeur null**, le pointeur est ignoré et **_freea** retourne immédiatement. Toute tentative de libération d’un pointeur non valide (pointeur vers un bloc de mémoire qui n’a pas été alloué par **_malloca**) peut affecter les demandes d’allocation ultérieures et provoquer des erreurs.

**_freea** appelle **gratuitement** en interne s’il détecte que la mémoire est allouée sur le tas. Un marqueur placé en mémoire à l’adresse qui précède immédiatement la mémoire allouée détermine si celle-ci est sur le tas ou la pile.

Si une erreur se produit lors de la libération de la mémoire, **errno** est défini avec les informations du système d’exploitation sur la nature de la défaillance. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Une fois qu’un bloc de mémoire a été libéré, [_heapmin](heapmin.md) réduit la quantité de mémoire disponible sur le tas en fusionnant les régions inutilisées et en les libérant pour le système d’exploitation. La mémoire libérée qui n’est pas mise à la disposition du système d’exploitation est restaurée vers le pool libre et peut être réallouée.

Un appel à **_freea** doit accompagner tous les appels à **_malloca**. Il y a également une erreur pour appeler **_freea** deux fois sur la même mémoire. Lorsque l’application est liée à une version Debug des bibliothèques Runtime C, en particulier avec [_malloc_dbg](malloc-dbg.md) fonctionnalités activées en définissant **_CRTDBG_MAP_ALLOC**, il est plus facile de trouver des appels manquants ou dupliqués à **_freea**. Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**_freea** est marqué `__declspec(noalias)` , ce qui signifie que la fonction ne peut pas modifier les variables globales. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_freea**|\<stdlib.h> et \<malloc.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_malloca](malloca.md).

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[_malloca](malloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
