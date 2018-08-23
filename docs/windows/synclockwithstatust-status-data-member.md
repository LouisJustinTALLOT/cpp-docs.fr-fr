---
title: Synclockwithstatust::Status, données de membre | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_
dev_langs:
- C++
helpviewer_keywords:
- status_ data member
ms.assetid: 466fa336-b5ff-4d43-8efd-1e87e5fddf88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d4a9a65e7ba45d38084d1695932c3897de583f49
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610025"
---
# <a name="synclockwithstatuststatus-data-member"></a>SyncLockWithStatusT::status_, données de membre

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
DWORD status_;
```

## <a name="remarks"></a>Notes

Contient le résultat de l’opération d’attente sous-jacente après une opération de verrouillage sur un objet selon actuel **SyncLockWithStatusT** objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** corewrappers.h

**Namespace :** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Voir aussi

[SyncLockWithStatusT, classe](../windows/synclockwithstatust-class.md)