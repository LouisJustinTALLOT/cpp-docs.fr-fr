---
title: _query_new_mode
ms.date: 11/04/2016
api_name:
- _query_new_mode
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- query_new_mode
- _query_new_mode
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
ms.openlocfilehash: 59724dafdc6488596478d0b44b254c4f498fce99
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950112"
---
# <a name="_query_new_mode"></a>_query_new_mode

Retourne un entier indiquant le mode du nouveau gestionnaire défini par **_set_new_mode** pour **malloc**.

## <a name="syntax"></a>Syntaxe

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>Valeur de retour

Retourne le nouveau mode de gestionnaire actuel, à savoir 0 ou 1, pour **malloc**. Une valeur de retour de 1 indique que, en cas d’échec d’allocation de mémoire, **malloc** appelle la routine de nouveau gestionnaire ; une valeur de retour de 0 indique qu’elle ne l’est pas.

## <a name="remarks"></a>Notes

La C++ fonction **_query_new_mode** retourne un entier qui indique le nouveau mode de gestionnaire défini par C++ la fonction [_set_new_mode](set-new-mode.md) pour [malloc](malloc.md). Le nouveau mode de gestionnaire indique si, en cas d’échec d’allocation de mémoire, **malloc** doit appeler la routine de nouveau gestionnaire telle qu’elle est définie par [_set_new_handler](set-new-handler.md). Par défaut, **malloc** n’appelle pas la routine de nouveau gestionnaire en cas d’échec. Vous pouvez utiliser **_set_new_mode** pour remplacer ce comportement afin que l’opérateur **malloc** appelle la routine de nouveau gestionnaire de la même façon que le **nouvel** opérateur lorsqu’il ne parvient pas à allouer de la mémoire. Pour plus d’informations, consultez la description des [opérateurs new et delete](../../cpp/new-and-delete-operators.md) dans la Référence du langage C++.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_query_new_mode**|\<new.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
