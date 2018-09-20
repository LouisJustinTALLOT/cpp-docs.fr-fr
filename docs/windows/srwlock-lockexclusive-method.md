---
title: SRWLOCK::lockexclusive, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive
dev_langs:
- C++
helpviewer_keywords:
- LockExclusive method
ms.assetid: f361b672-fca6-45cc-a9b4-310cc0d23fdc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b8aa6927acc165870ebb8f2a6128eaabbb1b144c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413040"
---
# <a name="srwlocklockexclusive-method"></a>SRWLock::LockExclusive, méthode

Acquiert un **SRWLock** objet en mode exclusif.

## <a name="syntax"></a>Syntaxe

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Paramètres

*lock*<br/>
Pointeur vers un **SRWLock** objet.

## <a name="return-value"></a>Valeur de retour

Un **SRWLock** objet en mode exclusif.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[SRWLock, classe](../windows/srwlock-class.md)