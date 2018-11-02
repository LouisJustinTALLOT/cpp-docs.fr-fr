---
title: _msize
ms.date: 11/04/2016
apiname:
- _msize
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
- msize
- _msize
helpviewer_keywords:
- memory blocks
- msize function
- _msize function
ms.assetid: 02b1f89e-d0d7-4f12-938a-9eeba48a0f88
ms.openlocfilehash: 0321e42face817a0a9f12d780f72c86c67ba308d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477270"
---
# <a name="msize"></a>_msize

Retourne la taille d’un bloc de mémoire alloué dans le tas.

## <a name="syntax"></a>Syntaxe

```C
size_t _msize(
   void *memblock
);
```

### <a name="parameters"></a>Paramètres

*memblock*<br/>
Pointeur désignant le bloc de mémoire.

## <a name="return-value"></a>Valeur de retour

**_msize** retourne la taille (en octets) sous forme d’entier non signé.

## <a name="remarks"></a>Notes

Le **_msize** fonction retourne la taille, en octets, du bloc de mémoire alloué par un appel à **calloc**, **malloc**, ou **realloc**.

Lorsque l’application est liée à une version debug des bibliothèques Runtime C, **_msize** se résout en [_msize_dbg](msize-dbg.md). Pour plus d’informations sur la gestion du tas pendant le processus de débogage, consultez [Tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details).

Cette fonction valide son paramètre. Si *memblock* est un pointeur null, **_msize** appelle un gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’erreur est gérée, la fonction définit **errno** à **EINVAL** et retourne -1.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [realloc](realloc.md).

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[_expand](expand.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
