---
title: DerefHelper (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::DerefHelper
dev_langs:
- C++
helpviewer_keywords:
- DerefHelper structure
ms.assetid: 86ded58b-c3ee-4a4f-bb86-4f67b895d427
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 326974e935608c9b41866e61e72b7a85fc8cb0b2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598529"
---
# <a name="derefhelper-structure"></a>DerefHelper (structure)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename T
>
struct DerefHelper;

template <
   typename T
>
struct DerefHelper<T*>;
```

### <a name="parameters"></a>Paramètres

*T*  
Un paramètre de modèle.

## <a name="remarks"></a>Notes

Représenter un pointeur déréférencé au `T*` paramètre de modèle.

**DerefHelper** est utilisé dans une expression comme : `ComPtr<Details::DerefHelper<ProgressTraits::Arg1Type>::DerefType> operationInterface;`.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`DerefType`|Identificateur pour le paramètre de modèle déréférencé `T*`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`DerefHelper`

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)