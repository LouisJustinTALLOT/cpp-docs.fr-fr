---
title: AsyncStatusInternal (énumération)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: fe70ee1ac5d26ed15d2b497356fe941c72ec0c83
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564942"
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

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)