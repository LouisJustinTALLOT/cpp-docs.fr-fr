---
description: 'En savoir plus sur : énumération Canceltransitionpolicy,'
title: CancelTransitionPolicy, énumération
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
helpviewer_keywords:
- CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
ms.openlocfilehash: 8de995ed492f8f1260534b08b818b77d889d95fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344534"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy, énumération

Indique comment la tentative d’une opération asynchrone de passage à un état terminal terminé ou d’erreur doit se comporter en ce qui concerne un état annulé du client.

## <a name="syntax"></a>Syntaxe

```cpp
enum CancelTransitionPolicy;
```

## <a name="members"></a>Membres

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`RemainCanceled`|Si l’opération asynchrone est actuellement dans un état d’annulation demandé par le client, cela indique qu’elle reste dans l’état annulé, contrairement à un état terminal terminé ou erreur.|
|`TransitionFromCanceled`|Si l’opération asynchrone est actuellement dans un état d’annulation demandé par le client, cela indique que l’État doit passer de cet état annulé à l’état terminal de terminé ou à une erreur déterminée par l’appel qui utilise cet indicateur.|

## <a name="requirements"></a>Spécifications

**En-tête :** Async. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)
