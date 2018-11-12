---
title: _CrtSetBreakAlloc
ms.date: 11/04/2016
apiname:
- _CrtSetBreakAlloc
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
- CrtSetBreakAlloc
- _CrtSetBreakAlloc
helpviewer_keywords:
- CrtSetBreakAlloc function
- _CrtSetBreakAlloc function
ms.assetid: 33bfc6af-a9ea-405b-a29f-1c2d4d9880a1
ms.openlocfilehash: bbc4b0de553533dde95f37675b3c9234569e3505
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487826"
---
# <a name="crtsetbreakalloc"></a>_CrtSetBreakAlloc

Définit un point d'arrêt sur un numéro d'ordre d'allocation d'objet spécifié (version de débogage uniquement).

## <a name="syntax"></a>Syntaxe

```C
long _CrtSetBreakAlloc(
   long lBreakAlloc
);
```

### <a name="parameters"></a>Paramètres

*lBreakAlloc*<br/>
Numéro d'ordre d'allocation pour lequel le point d'arrêt est défini.

## <a name="return-value"></a>Valeur de retour

Retourne le numéro d'ordre d'allocation d'objet précédent qui avait un point d'arrêt défini.

## <a name="remarks"></a>Notes

**_CrtSetBreakAlloc** permet à une application effectuer la détection des fuites de mémoire en s’arrêtant à un point spécifique d’allocation de mémoire et en remontant à l’origine de la demande. La fonction utilise le numéro d'ordre d'allocation d'objet séquentiel assigné au bloc de mémoire au moment où il a été alloué dans le tas. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtSetBreakAlloc** sont supprimés lors du prétraitement.

Le numéro d’ordre d’allocation d’objet est stocké dans le champ *lRequest* de la structure **_CrtMemBlockHeader**, définie dans Crtdbg.h. Lorsque les informations sur un bloc de mémoire sont signalées par une des fonctions de vidage du débogage, ce numéro est placé entre accolades, comme {36}.

Pour plus d’informations sur la façon **_CrtSetBreakAlloc** peut être utilisé avec d’autres fonctions de gestion de mémoire, consultez [le suivi des demandes d’Allocation du tas](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version Debug du tas de base, consultez [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtSetBreakAlloc**|\<crtdbg.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Uniquement les versions de débogage des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

```C
// crt_setbrkal.c
// compile with: -D_DEBUG /MTd -Od -Zi -W3 /c /link -verbose:lib -debug

/*
* In this program, a call is made to the _CrtSetBreakAlloc routine
* to verify that the debugger halts program execution when it reaches
* a specified allocation number.
*/

#include <malloc.h>
#include <crtdbg.h>

int main( )
{
        long allocReqNum;
        char *my_pointer;

        /*
         * Allocate "my_pointer" for the first
         * time and ensure that it gets allocated correctly
         */
        my_pointer = malloc(10);
        _CrtIsMemoryBlock(my_pointer, 10, &allocReqNum, NULL, NULL);

        /*
         * Set a breakpoint on the allocation request
         * number for "my_pointer"
         */
        _CrtSetBreakAlloc(allocReqNum+2);

        /*
         * Alternate freeing and reallocating "my_pointer"
         * to verify that the debugger halts program execution
         * when it reaches the allocation request
         */
        free(my_pointer);
        my_pointer = malloc(10);
        free(my_pointer);
        my_pointer = malloc(10);
        free(my_pointer);
}
```

## <a name="see-also"></a>Voir aussi

[Routines de débogage](../../c-runtime-library/debug-routines.md)<br/>
