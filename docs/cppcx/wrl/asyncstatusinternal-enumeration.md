---
description: 'En savoir plus sur : énumération Asyncstatusinternal ('
title: AsyncStatusInternal (énumération)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
ms.openlocfilehash: 3227699a0e7b8933dc5839e65fb3489328d3b1f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175792"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal (énumération)

Prend en charge l’infrastructure WRL et n’est pas destiné à être utilisé directement à partir de votre code.

## <a name="syntax"></a>Syntaxe

```cpp
enum AsyncStatusInternal;
```

## <a name="remarks"></a>Notes

Spécifie un mappage entre les énumérations internes pour l’état des opérations asynchrones et l' `Windows::Foundation::AsyncStatus` énumération.

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

[Microsoft :: WRL ::D espace de noms étails](microsoft-wrl-details-namespace.md)
