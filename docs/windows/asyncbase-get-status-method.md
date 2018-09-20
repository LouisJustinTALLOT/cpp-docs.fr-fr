---
title: Asyncbase::get_status, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_Status
dev_langs:
- C++
helpviewer_keywords:
- get_Status method
ms.assetid: 9823ecb9-212e-471d-b76f-7b8f21208905
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c1bb13773736104354d6276fef0a731aa72f22d2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431240"
---
# <a name="asyncbasegetstatus-method"></a>AsyncBase::get_Status, méthode

Récupère une valeur qui indique l’état de l’opération asynchrone.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Paramètres

*status*<br/>
L’emplacement où l’état doit être stocké. Pour plus d’informations, consultez `Windows::Foundation::AsyncStatus` énumération.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.

## <a name="remarks"></a>Notes

Cette méthode implémente `IAsyncInfo::get_Status`.

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[AsyncBase, classe](../windows/asyncbase-class.md)