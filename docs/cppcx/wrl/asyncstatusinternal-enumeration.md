---
title: AsyncStatusInternal (énumération)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: 0eadd1e3a287feecd36b00b231b42c31218352c1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214147"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal (énumération)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
enum AsyncStatusInternal;
```

## <a name="remarks"></a>Notes

Spécifie un mappage entre les énumérations internes pour l’état des opérations asynchrones et l’énumération `Windows::Foundation::AsyncStatus`.

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

**En-tête :** Async. h

**Espace de noms :** Microsoft :: WRL ::D étails

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)
