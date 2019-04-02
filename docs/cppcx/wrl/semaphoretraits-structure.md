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
ms.openlocfilehash: e7bd2e5d0993c8e4be7223d98ffb1dbec14cbb74
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784647"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits (structure)

Définit les caractéristiques communes d’un `Semaphore` objet.

## <a name="syntax"></a>Syntaxe

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                               | Description
---------------------------------- | --------------------------------------
[SemaphoreTraits::Unlock](#unlock) | Contrôle de versions d’une ressource partagée.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::WRL::Wrappers::HandleTraits

## <a name="unlock"></a>SemaphoreTraits::Unlock

Contrôle de versions d’une ressource partagée.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Handle vers un `Semaphore` objet.

### <a name="remarks"></a>Notes

Si l’opération de déverrouillage est infructueuse, `Unlock()` émet une erreur qui indique la cause de l’échec.
