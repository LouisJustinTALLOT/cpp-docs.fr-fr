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
ms.openlocfilehash: 4005f0dc1f75b79650963efc9a6f9f7522bc3395
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476464"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits (structure)

Décrit les caractéristiques communes de la `SRWLock` classe en mode de verrou exclusif.

## <a name="syntax"></a>Syntaxe

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom   | Description
------ | --------------------------------------------------------------------------
`Type` | Synonyme pour un pointeur vers le [SRWLOCK](../windows/srwlock-class.md) classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                        | Description
----------------------------------------------------------- | --------------------------------------------------------------------
[SRWLockExclusiveTraits::GetInvalidValue](#getinvalidvalue) | Récupère un `SRWLockExclusiveTraits` objet qui est toujours non valide.
[SRWLockExclusiveTraits::Unlock](#unlock)                   | Libère le contrôle exclusif du spécifié `SRWLock` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SRWLockExclusiveTraits`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>SRWLockExclusiveTraits::GetInvalidValue

Récupère un `SRWLockExclusiveTraits` objet qui est toujours non valide.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valeur de retour

Objet `SRWLockExclusiveTraits` vide

## <a name="unlock"></a>SRWLockExclusiveTraits::Unlock

Libère le contrôle exclusif du spécifié `SRWLock` objet.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Paramètres

*SRWLOCK*<br/>
Handle vers un `SRWLock` objet.
