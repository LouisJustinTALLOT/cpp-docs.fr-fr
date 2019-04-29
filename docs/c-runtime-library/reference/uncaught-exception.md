---
title: __uncaught_exception
ms.date: 11/04/2016
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
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
ms.openlocfilehash: 19d1e18af27722d6f9da39ebaaf6c9415c281849
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268895"
---
# <a name="uncaughtexception"></a>__uncaught_exception

Indique si une ou plusieurs exceptions ont été levées, mais n’ont pas encore été traitées par le correspondantes **catch** de blocs à un [try-catch](../../cpp/try-throw-and-catch-statements-cpp.md) instruction.

## <a name="syntax"></a>Syntaxe

```cpp
bool __uncaught_exception(
   );
```

## <a name="return-value"></a>Valeur de retour

**true** à partir du moment, une exception est levée un **essayez** bloc jusqu'à ce que la mise en correspondance **catch** bloc est initialisé ; sinon, **false**.

## <a name="remarks"></a>Notes

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|__uncaught_exception|eh.h|

## <a name="see-also"></a>Voir aussi

[Instructions try, throw et catch (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)<br/>
