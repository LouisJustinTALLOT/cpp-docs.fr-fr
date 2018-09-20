---
title: Semaphore::Lock, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 0eef6ede-dc7d-4f09-a6c8-2f7d39d65bfa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2083992bcb444a10b495b7007c698499f9cd9628
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419163"
---
# <a name="semaphorelock-method"></a>Semaphore::Lock, méthode

Attend jusqu'à ce que l’objet actuel, ou le **sémaphore** objet associé au handle spécifié, est dans l’état signalé ou que l’intervalle de délai d’attente spécifié est écoulé.

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
Un handle vers un **sémaphore** objet.

## <a name="return-value"></a>Valeur de retour

`Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[Semaphore, classe](../windows/semaphore-class.md)