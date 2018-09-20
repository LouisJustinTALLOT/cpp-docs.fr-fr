---
title: Mutex::Lock, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 61d95072-b690-441e-a080-0bf94a733141
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8bb04b8be33f81931106574152d0ccb6ba535295
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427834"
---
# <a name="mutexlock-method"></a>Mutex::Lock, méthode

Attend jusqu'à ce que l’objet actuel, ou le **Mutex** objet associé au handle spécifié, versions le mutex ou l’intervalle de délai d’attente spécifié se soit écoulé.

## <a name="syntax"></a>Syntaxe

```cpp
SyncLock Lock(
   DWORD milliseconds = INFINITE
);

static SyncLock Lock(
   HANDLE h,
   DWORD milliseconds = INFINITE
);
```

### <a name="parameters"></a>Paramètres

*millisecondes*<br/>
L’intervalle de délai d’attente, en millisecondes. La valeur par défaut est INFINITE, qui attend indéfiniment.

*h*<br/>
Le handle d’un **Mutex** objet.

## <a name="return-value"></a>Valeur de retour

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[Mutex (classe)](../windows/mutex-class1.md)