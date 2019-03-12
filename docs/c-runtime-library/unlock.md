---
title: _unlock
ms.date: 11/04/2016
apiname:
- _unlock
apilocation:
- msvcrt.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- unlock
- _unlock
helpviewer_keywords:
- unlock function
- _unlock function
ms.assetid: 2eda2507-a134-4997-aa12-f2f8cb319e14
ms.openlocfilehash: aceac01608a3d62fc4ac9c3aaf1f530584e1a3fa
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740400"
---
# <a name="unlock"></a>_unlock

Libère un verrou multithread.

> [!IMPORTANT]
>  Cette fonction est obsolète. Depuis Visual Studio 2015, elle n’est pas disponible dans la bibliothèque CRT.

## <a name="syntax"></a>Syntaxe

```
void __cdecl _unlock(
   int locknum
);
```

#### <a name="parameters"></a>Paramètres

*locknum*<br/>
[in] Identificateur du verrou à libérer.

## <a name="requirements"></a>Spécifications

**Source :** mlock.c

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des fonctions](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_lock](../c-runtime-library/lock.md)
