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
ms.openlocfilehash: 792f9f6c6d76097459498c43068f46d86b2e2349
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401483"
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

*status*<br/>
L’emplacement où cette opération stocke l’état actuel.

## <a name="remarks"></a>Notes

Cette opération est thread-safe.

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[AsyncBase, classe](../windows/asyncbase-class.md)<br/>
[AsyncStatusInternal, énumération](../windows/asyncstatusinternal-enumeration.md)