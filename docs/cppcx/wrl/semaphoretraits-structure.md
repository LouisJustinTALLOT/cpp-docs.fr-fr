---
description: 'En savoir plus sur : structure SemaphoreTraits'
title: SemaphoreTraits (structure)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock method
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
ms.openlocfilehash: 5779a30d22fd2d32e57f96f752bb52e2bf469cd8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97135224"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits (structure)

Définit les caractéristiques communes d’un `Semaphore` objet.

## <a name="syntax"></a>Syntaxe

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                               | Description
---------------------------------- | --------------------------------------
[SemaphoreTraits :: Unlock](#unlock) | Libère le contrôle d’une ressource partagée.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>Spécifications

**En-tête :** corewrappers. h

**Espace de noms :** Microsoft :: WRL :: wrappers :: HandleTraits

## <a name="semaphoretraitsunlock"></a><a name="unlock"></a> SemaphoreTraits :: Unlock

Libère le contrôle d’une ressource partagée.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Handle vers un `Semaphore` objet.

### <a name="remarks"></a>Notes

Si l’opération de déverrouillage échoue, `Unlock()` émet une erreur qui indique la cause de l’échec.
