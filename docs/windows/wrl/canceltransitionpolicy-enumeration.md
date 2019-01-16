---
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
ms.openlocfilehash: cfd8e25f98ec1001a8fbd287eaec12408b9f240e
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335951"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy, énumération

Indique la façon dont une opération asynchrone tentative du passage à un état terminal de terminé ou erreur doit se comporter en ce qui concerne un client a demandé l’état annulé.

## <a name="syntax"></a>Syntaxe

```cpp
enum CancelTransitionPolicy;
```

## <a name="members"></a>Membres

### <a name="values"></a>Valeurs

|Nom|Description|
|----------|-----------------|
|`RemainCanceled`|Si l’opération asynchrone est en cours d’un client a demandé l’état annulé, cela indique qu’il reste à l’état annulé par opposition à la transition vers un terminal terminée ou l’état d’erreur.|
|`TransitionFromCanceled`|Si l’opération asynchrone est en cours d’un client a demandé l’état annulé, cela indique qu’état doit passer de celle état annulé à l’état terminal de terminé ou erreur, tel que déterminé par l’appel qui utilise cet indicateur.|

## <a name="requirements"></a>Spécifications

**En-tête :** async.h

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)