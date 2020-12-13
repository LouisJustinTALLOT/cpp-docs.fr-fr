---
description: 'En savoir plus sur : _query_new_handler'
title: _query_new_handler
ms.date: 11/04/2016
api_name:
- _query_new_handler
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
- _query_new_handler
- query_new_handler
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
ms.openlocfilehash: 8479ad1ffc6ec03d3cff82df645255fc69b16257
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137148"
---
# <a name="_query_new_handler"></a>_query_new_handler

Retourne l’adresse de la routine de nouveau gestionnaire actuelle.

## <a name="syntax"></a>Syntaxe

```C
_PNH _query_new_handler(
   void
);
```

## <a name="return-value"></a>Valeur de retour

Retourne l’adresse de la routine actuelle du nouveau gestionnaire telle qu’elle est définie par **_set_new_handler**.

## <a name="remarks"></a>Notes

La fonction de **_Query_new_handler** c++ retourne l’adresse de la fonction de gestion des exceptions actuelle définie par la fonction de [_set_new_handler](set-new-handler.md) c++. **_set_new_handler** est utilisé pour spécifier une fonction de gestion des exceptions qui doit prendre le contrôle si l' **`new`** opérateur ne parvient pas à allouer de la mémoire. Pour plus d’informations, consultez la description des [opérateurs new et delete](../../cpp/new-and-delete-operators.md) dans la Référence du langage C++.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_query_new_handler**|\<new.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
