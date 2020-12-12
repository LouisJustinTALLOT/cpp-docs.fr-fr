---
description: 'En savoir plus sur : structure SRWLockExclusiveTraits'
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
ms.openlocfilehash: 135d4f866d1ca32ee9170ef9844cb0bf8d38c29a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186205"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits (structure)

Décrit les caractéristiques communes de la `SRWLock` classe en mode de verrouillage exclusif.

## <a name="syntax"></a>Syntaxe

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom   | Description
------ | --------------------------------------------------------------------------
`Type` | Synonyme d’un pointeur vers la classe [SRWLock](srwlock-class.md) .

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                        | Description
----------------------------------------------------------- | --------------------------------------------------------------------
[SRWLockExclusiveTraits :: Getinvalidvalue,](#getinvalidvalue) | Récupère un `SRWLockExclusiveTraits` objet qui est toujours non valide.
[SRWLockExclusiveTraits :: Unlock](#unlock)                   | Libère le contrôle exclusif de l' `SRWLock` objet spécifié.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SRWLockExclusiveTraits`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers :: HandleTraits

## <a name="srwlockexclusivetraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a> SRWLockExclusiveTraits :: Getinvalidvalue,

Récupère un `SRWLockExclusiveTraits` objet qui est toujours non valide.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valeur renvoyée

Objet `SRWLockExclusiveTraits` vide.

## <a name="srwlockexclusivetraitsunlock"></a><a name="unlock"></a> SRWLockExclusiveTraits :: Unlock

Libère le contrôle exclusif de l' `SRWLock` objet spécifié.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Paramètres

*SRWLock*<br/>
Handle vers un `SRWLock` objet.
