---
description: 'En savoir plus sur : structure SRWLockSharedTraits'
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
ms.openlocfilehash: 2cdfbd584adeffc9dedd8504d9183d6c5d4c1a95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135120"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits (structure)

Décrit les caractéristiques communes de la `SRWLock` classe en mode de verrouillage partagé.

## <a name="syntax"></a>Syntaxe

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom   | Description
------ | --------------------------------------------------------------------------
`Type` | Synonyme d’un pointeur vers la classe [SRWLock](srwlock-class.md) .

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                     | Description
-------------------------------------------------------- | -----------------------------------------------------------------
[SRWLockSharedTraits :: Getinvalidvalue,](#getinvalidvalue) | Récupère un `SRWLockSharedTraits` objet qui est toujours non valide.
[SRWLockSharedTraits :: Unlock](#unlock)                   | Libère le contrôle exclusif de l' `SRWLock` objet spécifié.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SRWLockSharedTraits`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers :: HandleTraits

## <a name="srwlocksharedtraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a> SRWLockSharedTraits :: Getinvalidvalue,

Récupère un `SRWLockSharedTraits` objet qui est toujours non valide.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valeur renvoyée

Handle d’un `SRWLockSharedTraits` objet.

## <a name="srwlocksharedtraitsunlock"></a><a name="unlock"></a> SRWLockSharedTraits :: Unlock

Libère le contrôle exclusif de l' `SRWLock` objet spécifié.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Paramètres

*SRWLock*<br/>
Handle d’un `SRWLock` objet.
