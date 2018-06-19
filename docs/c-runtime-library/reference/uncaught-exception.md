---
title: __uncaught_exception | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __uncaught_exception
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
- __uncaught_exception
dev_langs:
- C++
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fcae75a5d25710866f781d766cfd77eceb977649
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408213"
---
# <a name="uncaughtexception"></a>__uncaught_exception

Indique si une ou plusieurs exceptions ont été levées, mais n’ont pas encore été traitées par le correspondant **catch** bloc d’un [try-catch](../../cpp/try-throw-and-catch-statements-cpp.md) instruction.

## <a name="syntax"></a>Syntaxe

```cpp
bool __uncaught_exception(
   );
```

## <a name="return-value"></a>Valeur de retour

**true** à partir de l’heure, une exception est levée un **essayez** blocage jusqu'à la mise en correspondance **catch** bloc est initialisé ; sinon, **false**.

## <a name="remarks"></a>Notes

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|__uncaught_exception|eh.h|

## <a name="see-also"></a>Voir aussi

[Instructions try, throw et catch (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)<br/>
