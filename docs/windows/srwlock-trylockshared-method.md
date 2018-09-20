---
title: SRWLOCK::trylockshared, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
dev_langs:
- C++
helpviewer_keywords:
- TryLockShared method
ms.assetid: 10cc198d-39a0-4d18-aa78-706744948668
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 985629f224f199d1b1f095847e64cc67fa5a97f9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388461"
---
# <a name="srwlocktrylockshared-method"></a>SRWLock::TryLockShared, méthode

Tente d’acquérir un **SRWLock** objet en mode partagé pour la valeur actuelle ou spécifiée **SRWLock** objet.

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Pointeur vers un **SRWLock** objet.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, une **SRWLock** objet dans le mode partagé et le thread appelant prend possession du verrou. Sinon, un **SRWLock** objet dont l’état n’est pas valide.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[SRWLock, classe](../windows/srwlock-class.md)