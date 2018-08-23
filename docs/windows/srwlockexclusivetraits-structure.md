---
title: SRWLockExclusiveTraits (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockExclusiveTraits structure
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 542ad92aa636c934e3250817931dd7f31d1fe85b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601601"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits (structure)

Décrit les caractéristiques communes de la `SRWLock` classe en mode de verrou exclusif.

## <a name="syntax"></a>Syntaxe

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`Type`|Synonyme pour un pointeur vers le [SRWLOCK](../windows/srwlock-class.md) classe.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[SRWLockExclusiveTraits::GetInvalidValue, méthode](../windows/srwlockexclusivetraits-getinvalidvalue-method.md)|Récupère un **SRWLockExclusiveTraits** objet qui est toujours non valide.|
|[SRWLockExclusiveTraits::Unlock, méthode](../windows/srwlockexclusivetraits-unlock-method.md)|Libère le contrôle exclusif du spécifié `SRWLock` objet.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SRWLockExclusiveTraits`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers::HandleTraits, espace de noms](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)