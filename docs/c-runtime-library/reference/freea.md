---
title: _freea
ms.date: 11/04/2016
apiname:
- _freea
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
- freea
- _freea
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
ms.openlocfilehash: ac9c5528755898b0de131bccf94185b501b0e720
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605892"
---
# <a name="freea"></a>_freea

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

## <a name="return-value"></a>Valeur de retour

Aucun

## <a name="remarks"></a>Notes

Le **_freea** fonction libère un bloc de mémoire (*memblock*) qui a été précédemment alloué par un appel à [_malloca](malloca.md). **_freea** vérifie si la mémoire a été allouée sur le tas ou la pile. Si elle a été allouée sur la pile, **_freea** ne fait rien. Si elle a été allouée sur le tas, le nombre d’octets libérés est équivalent au nombre d’octets demandés quand le bloc a été alloué. Si *memblock* est **NULL**, le pointeur est ignoré et **_freea** retourne immédiatement. Tenter de libérer un pointeur non valide (un pointeur désignant un bloc de mémoire qui n’était pas alloué par **_malloca**) peut affecter les demandes d’allocation ultérieures et provoquer des erreurs.

**_freea** appels **gratuit** en interne si elle détecte que la mémoire est allouée sur le tas. Un marqueur placé en mémoire à l’adresse qui précède immédiatement la mémoire allouée détermine si celle-ci est sur le tas ou la pile.

Si une erreur se produit pendant la libération de la mémoire, **errno** est définie avec des informations sur la nature de la défaillance du système d’exploitation. Pour plus d’informations, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Une fois qu’un bloc de mémoire a été libéré, [_heapmin](heapmin.md) réduit la quantité de mémoire disponible sur le tas en fusionnant les régions inutilisées et en les libérant pour le système d’exploitation. La mémoire libérée qui n’est pas mise à la disposition du système d’exploitation est restaurée vers le pool libre et peut être réallouée.

Un appel à **_freea** doit accompagner tous les appels à **_malloca**. Il est également une erreur d’appeler **_freea** deux fois sur la même mémoire. Lorsque l’application est liée à une version debug des bibliothèques Runtime C, en particulier avec [_malloc_dbg](malloc-dbg.md) fonctionnalités activées en définissant **_CRTDBG_MAP_ALLOC**, il est plus facile à trouver manquant ou dupliqué d’appels à **_freea**. Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

**_freea** est marqué `__declspec(noalias)`, ce qui signifie que la fonction ne peut ne pas modifier les variables globales. Pour plus d’informations, consultez [noalias](../../cpp/noalias.md).

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**_freea**|\<stdlib.h> et \<malloc.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
