---
title: MutexTraits (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
dev_langs:
- C++
helpviewer_keywords:
- MutexTraits structure
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 529265c4b1e5f510a92295a1ceff6d0a012163fe
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584169"
---
# <a name="mutextraits-structure"></a>MutexTraits (structure)

Définit les caractéristiques communes de la [Mutex](../windows/mutex-class1.md) classe.

## <a name="syntax"></a>Syntaxe

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[MutexTraits::Unlock, méthode](../windows/mutextraits-unlock-method.md)|Libère le contrôle exclusif d’une ressource partagée.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers::HandleTraits, espace de noms](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)