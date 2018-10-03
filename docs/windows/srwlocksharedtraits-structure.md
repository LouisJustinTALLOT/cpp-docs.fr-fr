---
title: SRWLockSharedTraits (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock method
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5cfebfd1a6ccb1f243b534c9693a4402de574f17
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48233672"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits (structure)

Décrit les caractéristiques communes de la `SRWLock` classe en mode de verrou partagé.

## <a name="syntax"></a>Syntaxe

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

Nom   | Description
------ | --------------------------------------------------------------------------
`Type` | Synonyme pour un pointeur vers le [SRWLOCK](../windows/srwlock-class.md) classe.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                     | Description
-------------------------------------------------------- | -----------------------------------------------------------------
[SRWLockSharedTraits::GetInvalidValue](#getinvalidvalue) | Récupère un `SRWLockSharedTraits` objet qui est toujours non valide.
[SRWLockSharedTraits::Unlock](#unlock)                   | Libère le contrôle exclusif du spécifié `SRWLock` objet.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SRWLockSharedTraits`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>SRWLockSharedTraits::GetInvalidValue

Récupère un `SRWLockSharedTraits` objet qui est toujours non valide.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valeur de retour

Un handle vers un `SRWLockSharedTraits` objet.

## <a name="unlock"></a>SRWLockSharedTraits::Unlock

Libère le contrôle exclusif du spécifié `SRWLock` objet.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Paramètres

*SRWLOCK*<br/>
Un handle vers un `SRWLock` objet.
