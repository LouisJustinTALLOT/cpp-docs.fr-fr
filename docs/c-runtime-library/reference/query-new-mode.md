---
title: _query_new_mode
ms.date: 11/04/2016
apiname:
- _query_new_mode
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
- query_new_mode
- _query_new_mode
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
ms.openlocfilehash: 327f22c847793316bd126721b4a66846d7da84dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358071"
---
# <a name="querynewmode"></a>_query_new_mode

Retourne un entier indiquant le mode de nouveau gestionnaire défini par **_set_new_mode** pour **malloc**.

## <a name="syntax"></a>Syntaxe

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>Valeur de retour

Retourne le mode Gestionnaire nouveau actuel, à savoir 0 ou 1, pour **malloc**. Une valeur de retour 1 indique qui, en cas d’échec d’allocation de mémoire, **malloc** appelle la routine de nouveau gestionnaire ; une valeur de retour 0 indique qu’il n’existe pas.

## <a name="remarks"></a>Notes

Le C++ **_query_new_mode** fonction retourne un entier qui indique le mode de nouveau gestionnaire défini par le C++ [_set_new_mode](set-new-mode.md) fonctionner pour [malloc](malloc.md). Le nouveau mode de gestionnaire indique si, en cas d’échec d’allocation de mémoire, **malloc** consiste à appeler la routine de nouveau gestionnaire telle que définie par [_set_new_handler](set-new-handler.md). Par défaut, **malloc** n’appelle pas la routine de nouveau gestionnaire en cas d’échec. Vous pouvez utiliser **_set_new_mode** pour remplacer ce comportement par conséquent, qui en cas d’échec **malloc** appelle la routine de nouveau gestionnaire de la même façon que le **nouveau** opérateur s’il ne parvient pas à allouer de la mémoire. Pour plus d’informations, consultez la description des [opérateurs new et delete](../../cpp/new-and-delete-operators.md) dans la Référence du langage C++.

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
