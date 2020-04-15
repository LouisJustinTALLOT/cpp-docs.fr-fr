---
title: SRWLockExclusiveTraits (structure)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock method
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
ms.openlocfilehash: eb7b30915d6061e8470601df33fecec310d1bbca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374308"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits (structure)

Décrit les caractéristiques `SRWLock` communes de la classe en mode verrou exclusif.

## <a name="syntax"></a>Syntaxe

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom   | Description
------ | --------------------------------------------------------------------------
`Type` | Synonyme d’un pointeur de la classe [SRWLOCK.](srwlock-class.md)

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                        | Description
----------------------------------------------------------- | --------------------------------------------------------------------
[SRWLockExclusiveTraits::GetInvalidValue](#getinvalidvalue) | Récupère un `SRWLockExclusiveTraits` objet qui est toujours invalide.
[SRWLockExclusiveTraits::Unlock](#unlock)                   | Communiqués contrôle exclusif `SRWLock` de l’objet spécifié.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SRWLockExclusiveTraits`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="srwlockexclusivetraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>SRWLockExclusiveTraits::GetInvalidValue

Récupère un `SRWLockExclusiveTraits` objet qui est toujours invalide.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valeur de retour

Objet `SRWLockExclusiveTraits` vide.

## <a name="srwlockexclusivetraitsunlock"></a><a name="unlock"></a>SRWLockExclusiveTraits::Unlock

Communiqués contrôle exclusif `SRWLock` de l’objet spécifié.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Paramètres

*srwlock (srwlock)*<br/>
Manipuler à `SRWLock` un objet.
