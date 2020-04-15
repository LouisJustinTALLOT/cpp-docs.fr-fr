---
title: MutexTraits (structure)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock method
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
ms.openlocfilehash: 6d4ba08ab1884e8584b0e98e931d2d63cdac5aec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371247"
---
# <a name="mutextraits-structure"></a>MutexTraits (structure)

Définit les caractéristiques communes de la classe [Mutex.](mutex-class.md)

## <a name="syntax"></a>Syntaxe

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                           | Description
------------------------------ | ------------------------------------------------
[MutexTraits::Unlock](#unlock) | Libère le contrôle exclusif d’une ressource partagée.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>Spécifications

**En-tête:** corewrappers.h

**Espace nom:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="mutextraitsunlock-method"></a><a name="unlock"></a>MutexTraits::Méthode de déverrouillage

Libère le contrôle exclusif d’une ressource partagée.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Manipuler à un objet mutex.
