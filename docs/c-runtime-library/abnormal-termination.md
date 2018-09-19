---
title: _abnormal_termination | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _abnormal_termination
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _abnormal_termination
dev_langs:
- C++
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e311c27d61eca82019f8069b0984557af02c74a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028205"
---
# <a name="abnormaltermination"></a>_abnormal_termination

Indique si le bloc `__finally` d’une [instruction try-finally](../cpp/try-finally-statement.md) est entré pendant que le système exécute une liste interne des gestionnaires de terminaisons.

## <a name="syntax"></a>Syntaxe

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>Valeur de retour

`true` si le système *déroule* la pile ; sinon, `false`.

## <a name="remarks"></a>Notes

Il s’agit d’une fonction interne utilisée pour gérer les exceptions de déroulement ; elle n’a pas vocation à être appelée à partir du code utilisateur.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>Voir aussi

[Instruction try-finally](../cpp/try-finally-statement.md)