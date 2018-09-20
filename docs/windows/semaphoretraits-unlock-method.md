---
title: Semaphoretraits::Unlock, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 4e0ea808-b70d-43f7-81ef-998c3b34e3a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c9519fb79bf8229578319fc1f3890f5d2e19442a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448275"
---
# <a name="semaphoretraitsunlock-method"></a>SemaphoreTraits::Unlock, méthode

Contrôle de versions d’une ressource partagée.

## <a name="syntax"></a>Syntaxe

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Handle vers un **sémaphore** objet.

## <a name="remarks"></a>Notes

Si l’opération de déverrouillage est infructueuse, **Unlock()** émet une erreur qui indique la cause de l’échec.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>Voir aussi

[SemaphoreTraits, structure](../windows/semaphoretraits-structure.md)