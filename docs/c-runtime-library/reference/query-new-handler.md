---
title: _query_new_handler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _query_new_handler
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
- _query_new_handler
- query_new_handler
dev_langs:
- C++
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 340574a57bf1e6309ac9a5e1aa59b7e28632ae59
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400997"
---
# <a name="querynewhandler"></a>_query_new_handler

Retourne l’adresse de la routine de nouveau gestionnaire actuelle.

## <a name="syntax"></a>Syntaxe

```C
_PNH _query_new_handler(
   void
);
```

## <a name="return-value"></a>Valeur de retour

Retourne l’adresse de la routine actuelle du Gestionnaire de nouveau en tant que jeu par **_set_new_handler**.

## <a name="remarks"></a>Notes

C++ **_query_new_handler** fonction retourne l’adresse de la fonction actuelle de gestion des exceptions définie par le C++ [_set_new_handler](set-new-handler.md) (fonction). **_set_new_handler** est utilisée pour spécifier une fonction de gestion des exceptions qui consiste à prendre le contrôle si le **nouveau** opérateur ne peut pas allouer de mémoire. Pour plus d’informations, consultez la description des [opérateurs new et delete](../../cpp/new-and-delete-operators.md) dans la Référence du langage C++.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_query_new_handler**|\<new.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Allocation de mémoire](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
