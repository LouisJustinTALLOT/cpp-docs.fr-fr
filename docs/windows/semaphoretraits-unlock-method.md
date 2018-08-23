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
ms.openlocfilehash: e993c58ea6fc84e0b4001b488632858e5251d67b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583969"
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

*h*  
Handle vers un **sémaphore** objet.

## <a name="remarks"></a>Notes

Si l’opération de déverrouillage est infructueuse, **Unlock()** émet une erreur qui indique la cause de l’échec.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>Voir aussi

[SemaphoreTraits, structure](../windows/semaphoretraits-structure.md)