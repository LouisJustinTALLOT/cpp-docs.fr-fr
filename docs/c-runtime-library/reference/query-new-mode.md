---
title: _query_new_mode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8907b043e8b4441d6e5213a1d386dbc1a5a6910a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405716"
---
# <a name="querynewmode"></a>_query_new_mode

Retourne un entier qui indique le mode du nouveau gestionnaire défini par **_set_new_mode** pour **malloc**.

## <a name="syntax"></a>Syntaxe

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>Valeur de retour

Retourne le mode Gestionnaire nouvelle actuel, à savoir 0 ou 1, pour **malloc**. Une valeur de 1 indique que, en cas d’échec d’allocation de mémoire, de retour **malloc** appelle la routine du nouveau gestionnaire ; une valeur de retour de 0 indique qu’il n’existe pas.

## <a name="remarks"></a>Notes

C++ **_query_new_mode** fonction retourne un entier qui indique le nouveau mode de gestionnaire est défini par le C++ [_set_new_mode](set-new-mode.md) fonctionner pour [malloc](malloc.md). Le nouveau mode de gestionnaire indique que ce soit, sur les échecs d’allocation de mémoire, **malloc** consiste à appeler la routine du gestionnaire en tant que jeu par [_set_new_handler](set-new-handler.md). Par défaut, **malloc** n’appelle pas la routine de gestionnaire de nouveau en cas d’échec. Vous pouvez utiliser **_set_new_mode** pour remplacer ce comportement, qui en cas d’échec **malloc** appelle la routine du gestionnaire dans la même façon que la **nouveau** opérateur s’il ne parvient pas à allocation de mémoire. Pour plus d’informations, consultez la description des [opérateurs new et delete](../../cpp/new-and-delete-operators.md) dans la Référence du langage C++.

## <a name="requirements"></a>Spécifications

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
