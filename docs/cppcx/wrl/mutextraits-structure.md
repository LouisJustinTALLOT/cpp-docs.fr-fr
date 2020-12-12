---
description: 'En savoir plus sur : structure MutexTraits'
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
ms.openlocfilehash: e3dfcee1251794734ed5cf787096361403d80c7f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330823"
---
# <a name="mutextraits-structure"></a>MutexTraits (structure)

Définit les caractéristiques communes de la classe [mutex](mutex-class.md) .

## <a name="syntax"></a>Syntaxe

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                           | Description
------------------------------ | ------------------------------------------------
[MutexTraits :: Unlock](#unlock) | Libère le contrôle exclusif d’une ressource partagée.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers :: HandleTraits

## <a name="mutextraitsunlock-method"></a><a name="unlock"></a> MutexTraits :: Unlock, méthode

Libère le contrôle exclusif d’une ressource partagée.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Handle vers un objet Mutex.
