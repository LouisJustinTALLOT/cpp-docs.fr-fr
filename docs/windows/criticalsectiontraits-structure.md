---
title: CriticalSectionTraits (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
dev_langs:
- C++
helpviewer_keywords:
- CriticalSectionTraits structure
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6d15f65ecc2253556a6812cfb90ef78f90c7fb29
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594732"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits (structure)

Spécialise une `CriticalSection` objet pour prendre en charge une section critique non valide ou une fonction d’annulation d’une section critique.

## <a name="syntax"></a>Syntaxe

```
struct CriticalSectionTraits;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`Type`|Un **typedef** qui définit un pointeur vers une section critique. `Type` est défini en tant que `typedef CRITICAL_SECTION* Type;`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CriticalSectionTraits::GetInvalidValue, méthode](../windows/criticalsectiontraits-getinvalidvalue-method.md)|Spécialise une `CriticalSection` modèle afin que le modèle est toujours non valide.|
|[CriticalSectionTraits::Unlock, méthode](../windows/criticalsectiontraits-unlock-method.md)|Spécialise une `CriticalSection` modèle afin qu’il prend en charge la libération de la propriété de l’objet de section critique spécifié.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CriticalSectionTraits`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers::HandleTraits, espace de noms](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)