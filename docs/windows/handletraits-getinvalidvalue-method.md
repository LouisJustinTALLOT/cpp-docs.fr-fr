---
title: Handletraits::getinvalidvalue, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- GetInvalidValue method
ms.assetid: e95d2cc1-e70f-463f-8ff0-183cdeac1138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 82616b0fc8cda44ea501b87f6ac1c6e0eddbfb57
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609360"
---
# <a name="handletraitsgetinvalidvalue-method"></a>HANDLETraits::GetInvalidValue, méthode

Représente un handle non valide.

## <a name="syntax"></a>Syntaxe

```cpp
inline static HANDLE GetInvalidValue();
```

## <a name="return-value"></a>Valeur de retour

Retourne toujours INVALID_HANDLE_VALUE. (INVALID_HANDLE_VALUE est défini par Windows.)

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>Voir aussi

[HANDLETraits, structure](../windows/handletraits-structure.md)