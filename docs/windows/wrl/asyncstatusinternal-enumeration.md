---
title: AsyncStatusInternal (énumération)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: b38d58603eafeaa76c79873bbf375b4a3b405cdb
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336066"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal (énumération)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
enum AsyncStatusInternal;
```

## <a name="remarks"></a>Notes

Spécifie un mappage entre des énumérations internes pour l’état des opérations asynchrones et la `Windows::Foundation::AsyncStatus` énumération.

## <a name="members"></a>Membres

`_Created`<br/>
Équivaut à `::Windows::Foundation::AsyncStatus::Created`.

`_Started`<br/>
Équivaut à `::Windows::Foundation::AsyncStatus::Started`.

`_Completed`<br/>
Équivaut à `::Windows::Foundation::AsyncStatus::Completed`.

`_Cancelled`<br/>
Équivaut à `::Windows::Foundation::AsyncStatus::Cancelled`.

`_Error`<br/>
Équivaut à `::Windows::Foundation::AsyncStatus::Error`.

## <a name="requirements"></a>Spécifications

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)