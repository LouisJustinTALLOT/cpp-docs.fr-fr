---
description: 'En savoir plus sur : __uncaught_exception'
title: __uncaught_exception
ms.date: 1/14/2021
api_name:
- __uncaught_exception
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __uncaught_exception
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
ms.openlocfilehash: dd3fb85a0264005b0c26f1030046661c5b291972
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98243045"
---
# <a name="__uncaught_exception"></a>__uncaught_exception

Indique si une ou plusieurs exceptions ont été levées, mais n’ont pas encore été gérées par le **`catch`** bloc correspondant d’une instruction [try-catch](../../cpp/try-throw-and-catch-statements-cpp.md) .

## <a name="syntax"></a>Syntaxe

```cpp
bool __uncaught_exception(
   );
```

## <a name="return-value"></a>Valeur de retour

**`true`** à partir du moment où une exception est levée dans un **`try`** bloc jusqu’à ce que le **`catch`** bloc correspondant soit initialisé ; Sinon, **`false`** .

## <a name="remarks"></a>Notes

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|__uncaught_exception|eh.h|

## <a name="see-also"></a>Voir aussi

[Instructions try, throw et catch (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)<br/>
