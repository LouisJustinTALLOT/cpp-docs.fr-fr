---
title: '&lt;future&gt;, énumérations | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 6e228eb538a0d281dff8066390b0c6dd2e7ea4d8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843845"
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt;, énumérations

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[Lancement](#launch)|

## <a name="future_errc"></a>  future_errc, énumération

Fournit des noms symboliques pour toutes les erreurs signalées par la classe [future_error](../standard-library/future-error-class.md).

class future_errc { broken_promise, future_already_retrieved, promise_already_satisfied, no_state };

## <a name="future_status"></a>  future_status, énumération

Fournit les noms symboliques pour les raisons qu’une fonction d’attente chronométrée peut retourner.

```cpp
enum future_status{    ready,
    timeout,
 deferred};
```

## <a name="launch"></a>  launch, énumération

Représente un type de masque de bits qui décrit les modes possibles pour la fonction de modèle [async](../standard-library/future-functions.md#async).

class launch{ async, deferred };

## <a name="see-also"></a>Voir aussi

[\<future>](../standard-library/future.md)<br/>
