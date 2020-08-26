---
title: '&lt;future&gt;, énumérations'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 45dc3277b3f14b7f9dbb043cf9db1f1865d4e4c9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838020"
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt;, énumérations

[future_errc](#future_errc)\
[future_status](#future_status)\
[lancer](#launch)

## <a name="future_errc-enumeration"></a><a name="future_errc"></a> Énumération future_errc

Fournit des noms symboliques pour toutes les erreurs signalées par la classe [future_error](../standard-library/future-error-class.md).

```cpp
class future_errc {
   broken_promise,
   future_already_retrieved,
   promise_already_satisfied,
   no_state
   };
```

## <a name="future_status-enumeration"></a><a name="future_status"></a> Énumération future_status

Fournit les noms symboliques pour les raisons qu’une fonction d’attente chronométrée peut retourner.

```cpp
enum future_status{
    ready,
    timeout,
    deferred
};
```

## <a name="launch-enumeration"></a><a name="launch"></a> Launch, énumération

Représente un type de masque de bits qui décrit les modes possibles pour la fonction de modèle [async](../standard-library/future-functions.md#async).

```cpp
class launch{
   async,
   deferred
   };
```

## <a name="see-also"></a>Voir aussi

[\<future>](../standard-library/future.md)
