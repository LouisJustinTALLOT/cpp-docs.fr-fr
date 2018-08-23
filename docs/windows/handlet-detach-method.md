---
title: Handlet::Detach, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: f7df0f90-fafb-4d1b-a215-a6c62941f6b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b66d5c65dd084da564067cd62242b315f6da182
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591372"
---
# <a name="handletdetach-method"></a>HandleT::Detach, méthode

Dissocie actuel **HandleT** objet à partir de son handle sous-jacent.

## <a name="syntax"></a>Syntaxe

```cpp
typename HandleTraits::Type Detach();
```

## <a name="return-value"></a>Valeur de retour

Le handle sous-jacent.

## <a name="remarks"></a>Notes

Lorsque cette opération se termine, actuel **HandleT** est défini sur l’état non valide.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Voir aussi

[HandleT, classe](../windows/handlet-class.md)