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
ms.openlocfilehash: 9bc4071e5699610a664cbf01ca3e7d36d7effc5e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784419"
---
# <a name="mutextraits-structure"></a>MutexTraits (structure)

Définit les caractéristiques communes de la [Mutex](mutex-class.md) classe.

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

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::WRL::Wrappers::HandleTraits

## <a name="unlock"></a>Mutextraits::Unlock, méthode

Libère le contrôle exclusif d’une ressource partagée.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Handle vers un objet mutex.
