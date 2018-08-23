---
title: HANDLENullTraits (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits
dev_langs:
- C++
helpviewer_keywords:
- HANDLENullTraits structure
ms.assetid: 88a29a14-c516-40cb-a0ca-ee897a668623
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3a49a1a1ac4495c7697fc041f8fcf217850f09d8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609422"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits (structure)

Définit les caractéristiques communes d’un handle non initialisé.

## <a name="syntax"></a>Syntaxe

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`Type`|Synonyme de HANDLE.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[HANDLENullTraits::Close, méthode](../windows/handlenulltraits-close-method.md)|Ferme le handle spécifié.|
|[HANDLENullTraits::GetInvalidValue, méthode](../windows/handlenulltraits-getinvalidvalue-method.md)|Représente un handle non valide.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`HANDLENullTraits`

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Wrappers::HandleTraits, espace de noms](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)