---
title: '&lt;future&gt;, énumérations'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 0f1064fdf434560c3130d1254512470cc5bc1ee0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370696"
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt;, énumérations

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[Lancement](#launch)|

## <a name="future_errc-enumeration"></a><a name="future_errc"></a>future_errc Énumération

Fournit des noms symboliques pour toutes les erreurs signalées par la classe [future_error](../standard-library/future-error-class.md).

```cpp
class future_errc {
   broken_promise,
   future_already_retrieved,
   promise_already_satisfied,
   no_state
   };
```

## <a name="future_status-enumeration"></a><a name="future_status"></a>future_status Énumération

Fournit les noms symboliques pour les raisons qu’une fonction d’attente chronométrée peut retourner.

```cpp
enum future_status{
    ready,
    timeout,
    deferred
};
```

## <a name="launch-enumeration"></a><a name="launch"></a>lancer l’énumération

Représente un type de masque de bits qui décrit les modes possibles pour la fonction de modèle [async](../standard-library/future-functions.md#async).

```cpp
class launch{
   async,
   deferred
   };
```

## <a name="see-also"></a>Voir aussi

[\<>avenir](../standard-library/future.md)
