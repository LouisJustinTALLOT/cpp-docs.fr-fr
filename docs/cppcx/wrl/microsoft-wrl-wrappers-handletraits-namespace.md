---
title: Microsoft::WRL::Wrappers::HandleTraits, espace de noms
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
ms.openlocfilehash: b19cc426fc7c1b4fc6ec0638730d59998f8c108a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213731"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits, espace de noms

Décrit les caractéristiques des types de ressources basés sur les descripteurs courants.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL::Wrappers::HandleTraits;
```

## <a name="members"></a>Membres

### <a name="structures"></a>Structures

|Name|Description|
|----------|-----------------|
|[CriticalSectionTraits, structure](criticalsectiontraits-structure.md)|Spécialise un objet `CriticalSection` pour prendre en charge une section critique non valide ou une fonction pour libérer une section critique.|
|[EventTraits, structure](eventtraits-structure.md)|Définit les caractéristiques d’un handle de classe `Event`.|
|[FileHandleTraits, structure](filehandletraits-structure.md)|Définit les caractéristiques d’un descripteur de fichier.|
|[HANDLENullTraits, structure](handlenulltraits-structure.md)|Définit les caractéristiques communes d’un handle non initialisé.|
|[HANDLETraits, structure](handletraits-structure.md)|Définit les caractéristiques communes d’un handle.|
|[MutexTraits, structure](mutextraits-structure.md)|Définit les caractéristiques communes de la classe [mutex](mutex-class.md) .|
|[SemaphoreTraits, structure](semaphoretraits-structure.md)|Définit les caractéristiques communes d’un objet Semaphore.|
|[SRWLockExclusiveTraits, structure](srwlockexclusivetraits-structure.md)|Décrit les caractéristiques communes de la classe `SRWLock` en mode de verrouillage exclusif.|
|[SRWLockSharedTraits, structure](srwlocksharedtraits-structure.md)|Décrit les caractéristiques communes de la classe `SRWLock` en mode de verrouillage partagé.|

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers, espace de noms](microsoft-wrl-wrappers-namespace.md)
