---
title: _abnormal_termination
ms.date: 11/04/2016
api_name:
- _abnormal_termination
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _abnormal_termination
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
ms.openlocfilehash: b66cf0df998b4e33a9f3425fdf0f260d163f423b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944709"
---
# <a name="_abnormal_termination"></a>_abnormal_termination

Indique si le bloc `__finally` d’une [instruction try-finally](../cpp/try-finally-statement.md) est entré pendant que le système exécute une liste interne des gestionnaires de terminaisons.

## <a name="syntax"></a>Syntaxe

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>Valeur de retour

**true** si le système *déroule* la pile ; sinon, **false**.

## <a name="remarks"></a>Notes

Il s’agit d’une fonction interne utilisée pour gérer les exceptions de déroulement ; elle n’a pas vocation à être appelée à partir du code utilisateur.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>Voir aussi

[Instruction try-finally](../cpp/try-finally-statement.md)
