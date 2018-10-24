---
title: _lock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _lock
apilocation:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- lock
- _lock
dev_langs:
- C++
helpviewer_keywords:
- lock function
- _lock function
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38cd49dd483b556c8bda95e7a77109a9d4682e7c
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48233617"
---
# <a name="lock"></a>_lock

Acquiert un verrou multithread.

> [!IMPORTANT]
>  Cette fonction est obsolète. Depuis Visual Studio 2015, elle n’est pas disponible dans la bibliothèque CRT.

## <a name="syntax"></a>Syntaxe

```
void __cdecl _lock
   int locknum
);
```

#### <a name="parameters"></a>Paramètres

*locknum*<br/>
[in] Identificateur du verrou à acquérir.

## <a name="remarks"></a>Notes

Si le verrou a déjà été acquis, cette méthode acquiert néanmoins le verrou et provoque une erreur CRT interne. Si la méthode ne peut pas acquérir un verrou, elle se termine avec une erreur irrécupérable et affecte le code d’erreur sur `_RT_LOCK`.

## <a name="requirements"></a>Configuration requise

**Source :** mlock.c

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_unlock](../c-runtime-library/unlock.md)