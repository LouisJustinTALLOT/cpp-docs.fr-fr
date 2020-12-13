---
description: 'En savoir plus sur : _lock'
title: _lock
ms.date: 11/04/2016
api_name:
- _lock
api_location:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lock
- _lock
helpviewer_keywords:
- lock function
- _lock function
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
ms.openlocfilehash: 9b95c8b7ad0f0ce84348f9581d9acb611373a27b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331042"
---
# <a name="_lock"></a>_lock

Acquiert un verrou multithread.

> [!IMPORTANT]
> Cette fonction est obsolète. Depuis Visual Studio 2015, elle n’est pas disponible dans la bibliothèque CRT.

## <a name="syntax"></a>Syntaxe

```cpp
void __cdecl _lock
   int locknum
);
```

#### <a name="parameters"></a>Paramètres

*locknum*<br/>
[in] Identificateur du verrou à acquérir.

## <a name="remarks"></a>Notes

Si le verrou a déjà été acquis, cette méthode acquiert néanmoins le verrou et provoque une erreur CRT interne. Si la méthode ne peut pas acquérir un verrou, elle se termine avec une erreur irrécupérable et affecte le code d’erreur sur `_RT_LOCK`.

## <a name="requirements"></a>Spécifications

**Source :** mlock.c

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_unlock](../c-runtime-library/unlock.md)
