---
title: SemaphoreTraits (structure)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock method
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
ms.openlocfilehash: 11719576c9fc7b23f4cd318ee1b3ed9ca3f5edaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360737"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits (structure)

Définit les caractéristiques `Semaphore` communes d’un objet.

## <a name="syntax"></a>Syntaxe

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                               | Description
---------------------------------- | --------------------------------------
[SemaphoreTraits::Unlock](#unlock) | Communiqués de contrôle d’une ressource partagée.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="semaphoretraitsunlock"></a><a name="unlock"></a>SemaphoreTraits::Unlock

Communiqués de contrôle d’une ressource partagée.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Manipuler à `Semaphore` un objet.

### <a name="remarks"></a>Notes

Si l’opération de `Unlock()` déverrouillage est infructueuse, émet une erreur qui indique la cause de la défaillance.
