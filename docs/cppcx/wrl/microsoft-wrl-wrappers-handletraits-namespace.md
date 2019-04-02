---
title: Microsoft::WRL::Wrappers::HandleTraits, espace de noms
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
ms.openlocfilehash: 55e1dfea2d4075a5a37b9654a70e9ce74383ea53
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784614"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits, espace de noms

Décrit les caractéristiques des types courants de ressources basées sur le handle.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL::Wrappers::HandleTraits;
```

## <a name="members"></a>Membres

### <a name="structures"></a>Structures

|Nom|Description|
|----------|-----------------|
|[CriticalSectionTraits, structure](criticalsectiontraits-structure.md)|Spécialise une `CriticalSection` objet pour prendre en charge une section critique non valide ou une fonction d’annulation d’une section critique.|
|[EventTraits, structure](eventtraits-structure.md)|Définit les caractéristiques d’un `Event` handle de classe.|
|[FileHandleTraits, structure](filehandletraits-structure.md)|Définit les caractéristiques d’un descripteur de fichier.|
|[HANDLENullTraits, structure](handlenulltraits-structure.md)|Définit les caractéristiques communes d’un handle non initialisé.|
|[HANDLETraits, structure](handletraits-structure.md)|Définit les caractéristiques communes d’une poignée.|
|[MutexTraits, structure](mutextraits-structure.md)|Définit les caractéristiques communes de la [Mutex](mutex-class.md) classe.|
|[SemaphoreTraits, structure](semaphoretraits-structure.md)|Définit les caractéristiques communes d’un objet sémaphore.|
|[SRWLockExclusiveTraits, structure](srwlockexclusivetraits-structure.md)|Décrit les caractéristiques communes de la `SRWLock` classe en mode de verrou exclusif.|
|[SRWLockSharedTraits, structure](srwlocksharedtraits-structure.md)|Décrit les caractéristiques communes de la `SRWLock` classe en mode de verrou partagé.|

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Espace de noms :** Microsoft::wrl::wrappers

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers, espace de noms](microsoft-wrl-wrappers-namespace.md)