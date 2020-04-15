---
title: SRWLockSharedTraits (structure)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock method
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
ms.openlocfilehash: 0dc43d4b9c16145ed7a5abe03cddb598c59b1e94
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374298"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits (structure)

Décrit les caractéristiques `SRWLock` communes de la classe en mode verrouillage partagé.

## <a name="syntax"></a>Syntaxe

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom   | Description
------ | --------------------------------------------------------------------------
`Type` | Synonyme d’un pointeur de la classe [SRWLOCK.](srwlock-class.md)

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                     | Description
-------------------------------------------------------- | -----------------------------------------------------------------
[SRWLockSharedTraits::GetInvalidValue](#getinvalidvalue) | Récupère un `SRWLockSharedTraits` objet qui est toujours invalide.
[SRWLockSharedTraits::Unlock](#unlock)                   | Communiqués contrôle exclusif `SRWLock` de l’objet spécifié.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SRWLockSharedTraits`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="srwlocksharedtraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>SRWLockSharedTraits::GetInvalidValue

Récupère un `SRWLockSharedTraits` objet qui est toujours invalide.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valeur de retour

Une poignée `SRWLockSharedTraits` à un objet.

## <a name="srwlocksharedtraitsunlock"></a><a name="unlock"></a>SRWLockSharedTraits::Unlock

Communiqués contrôle exclusif `SRWLock` de l’objet spécifié.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Paramètres

*srwlock (srwlock)*<br/>
Une poignée `SRWLock` à un objet.
