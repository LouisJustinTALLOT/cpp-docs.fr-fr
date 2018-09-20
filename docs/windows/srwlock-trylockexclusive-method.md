---
title: SRWLOCK::trylockexclusive, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
dev_langs:
- C++
helpviewer_keywords:
- TryLockExclusive method
ms.assetid: 661e8b19-3058-4511-8742-c9fbb90412c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0deec4790d185a5c6b7a7bdcbd670b056fc6f03
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424103"
---
# <a name="srwlocktrylockexclusive-method"></a>SRWLock::TryLockExclusive, méthode

Tente d’acquérir un **SRWLock** objet en mode exclusif pour la valeur actuelle ou spécifiée **SRWLock** objet. Si l’appel réussit, le thread appelant prend possession du verrou.

## <a name="syntax"></a>Syntaxe

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Pointeur vers un **SRWLock** objet.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, une **SRWLock** objet en mode exclusif et que le thread appelant prend possession du verrou. Sinon, un **SRWLock** objet dont l’état n’est pas valide.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[SRWLock, classe](../windows/srwlock-class.md)