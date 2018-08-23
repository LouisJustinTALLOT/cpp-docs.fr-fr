---
title: Asyncbase::currentStatus, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CurrentStatus
dev_langs:
- C++
helpviewer_keywords:
- CurrentStatus method
ms.assetid: 26ee4c4a-6525-4a5f-b49c-3ca40c365eb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 193f4d26f7e163707092f3d0bc8f981a02611a22
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603700"
---
# <a name="asyncbasecurrentstatus-method"></a>AsyncBase::CurrentStatus, méthode

Récupère l’état de l’opération asynchrone actuelle.

## <a name="syntax"></a>Syntaxe

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Paramètres

*status*  
L’emplacement où cette opération stocke l’état actuel.

## <a name="remarks"></a>Notes

Cette opération est thread-safe.

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[AsyncBase, classe](../windows/asyncbase-class.md)  
[AsyncStatusInternal, énumération](../windows/asyncstatusinternal-enumeration.md)