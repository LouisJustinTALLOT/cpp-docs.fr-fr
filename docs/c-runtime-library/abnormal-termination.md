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
ms.openlocfilehash: a963f1059eccaddce9ec01cd53a07df668ee46c6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213656"
---
# <a name="_abnormal_termination"></a>_abnormal_termination

Indique si le **`__finally`** bloc d’une [instruction try-finally](../cpp/try-finally-statement.md) est entré pendant que le système exécute une liste interne de gestionnaires de terminaisons.

## <a name="syntax"></a>Syntaxe

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>Valeur de retour

**`true`** Si le système *déroulera* la pile ; Sinon, **`false`** .

## <a name="remarks"></a>Notes

Il s’agit d’une fonction interne utilisée pour gérer les exceptions de déroulement ; elle n’a pas vocation à être appelée à partir du code utilisateur.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>Voir aussi

[try-finally, instruction](../cpp/try-finally-statement.md)
