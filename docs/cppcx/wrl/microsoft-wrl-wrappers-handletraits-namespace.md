---
description: 'En savoir plus sur : Microsoft :: WRL :: wrappers :: HandleTraits, espace de noms'
title: Microsoft::WRL::Wrappers::HandleTraits, espace de noms
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
ms.openlocfilehash: 4bbc970a6d3445e8acda752be1a2030ee99759a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178054"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits, espace de noms

Décrit les caractéristiques des types de ressources basés sur les descripteurs courants.

## <a name="syntax"></a>Syntaxe

```cpp
namespace Microsoft::WRL::Wrappers::HandleTraits;
```

## <a name="members"></a>Membres

### <a name="structures"></a>Structures

|Nom|Description|
|----------|-----------------|
|[CriticalSectionTraits (structure)](criticalsectiontraits-structure.md)|Spécialise un `CriticalSection` objet pour prendre en charge une section critique non valide ou une fonction pour libérer une section critique.|
|[EventTraits (structure)](eventtraits-structure.md)|Définit les caractéristiques d’un `Event` handle de classe.|
|[FileHandleTraits (structure)](filehandletraits-structure.md)|Définit les caractéristiques d’un descripteur de fichier.|
|[HANDLENullTraits (structure)](handlenulltraits-structure.md)|Définit les caractéristiques communes d’un handle non initialisé.|
|[HANDLETraits (structure)](handletraits-structure.md)|Définit les caractéristiques communes d’un handle.|
|[MutexTraits (structure)](mutextraits-structure.md)|Définit les caractéristiques communes de la classe [mutex](mutex-class.md) .|
|[SemaphoreTraits (structure)](semaphoretraits-structure.md)|Définit les caractéristiques communes d’un objet Semaphore.|
|[SRWLockExclusiveTraits (structure)](srwlockexclusivetraits-structure.md)|Décrit les caractéristiques communes de la `SRWLock` classe en mode de verrouillage exclusif.|
|[SRWLockSharedTraits (structure)](srwlocksharedtraits-structure.md)|Décrit les caractéristiques communes de la `SRWLock` classe en mode de verrouillage partagé.|

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL :: wrappers, espace de noms](microsoft-wrl-wrappers-namespace.md)
