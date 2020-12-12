---
description: 'En savoir plus sur : _CrtSetBreakAlloc'
title: _CrtSetBreakAlloc
ms.date: 11/04/2016
api_name:
- _CrtSetBreakAlloc
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
- CrtSetBreakAlloc
- _CrtSetBreakAlloc
helpviewer_keywords:
- CrtSetBreakAlloc function
- _CrtSetBreakAlloc function
ms.assetid: 33bfc6af-a9ea-405b-a29f-1c2d4d9880a1
ms.openlocfilehash: 07db47aa23fe95e86b3341813137643b81f57fbc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319597"
---
# <a name="_crtsetbreakalloc"></a>_CrtSetBreakAlloc

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

## <a name="return-value"></a>Valeur renvoyée

Retourne le numéro d'ordre d'allocation d'objet précédent qui avait un point d'arrêt défini.

## <a name="remarks"></a>Notes

**_CrtSetBreakAlloc** permet à une application d’effectuer la détection des fuites de mémoire en s’arrêtant à un point d’allocation de mémoire spécifique et en remontant à l’origine de la demande. La fonction utilise le numéro d'ordre d'allocation d'objet séquentiel assigné au bloc de mémoire au moment où il a été alloué dans le tas. Lorsque [_DEBUG](../../c-runtime-library/debug.md) n’est pas défini, les appels à **_CrtSetBreakAlloc** sont supprimés lors du prétraitement.

Le numéro d’ordre d’allocation d’objet est stocké dans le champ *lRequest* de la structure **_CrtMemBlockHeader**, définie dans Crtdbg.h. Quand les informations sur un bloc de mémoire sont signalées par l’une des fonctions de vidage du débogage, ce nombre est placé entre accolades, par exemple {36} .

Pour plus d’informations sur la façon dont **_CrtSetBreakAlloc** peut être utilisé avec d’autres fonctions de gestion de la mémoire, consultez [suivi des demandes d’allocation de tas](/visualstudio/debugger/crt-debug-heap-details). Pour plus d’informations sur la façon dont les blocs de mémoire sont alloués, initialisés et gérés dans la version Debug du tas de base, consultez [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_CrtSetBreakAlloc**|\<crtdbg.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

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
