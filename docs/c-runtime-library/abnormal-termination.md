---
title: _abnormal_termination
ms.date: 11/04/2016
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
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
ms.openlocfilehash: 213938fa830f0a924fa954d4a36a39b544473dd4
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741289"
---
# <a name="abnormaltermination"></a>_abnormal_termination

Indique si le bloc `__finally` d’une [instruction try-finally](../cpp/try-finally-statement.md) est entré pendant que le système exécute une liste interne des gestionnaires de terminaisons.

## <a name="syntax"></a>Syntaxe

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>Valeur de retour

**true** si le système *déroule* la pile ; sinon, **false**.

## <a name="remarks"></a>Remarques

Il s’agit d’une fonction interne utilisée pour gérer les exceptions de déroulement ; elle n’a pas vocation à être appelée à partir du code utilisateur.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>Voir aussi

[Instruction try-finally](../cpp/try-finally-statement.md)
