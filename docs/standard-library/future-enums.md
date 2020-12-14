---
description: 'En savoir plus sur &lt; : &gt; énumérations futures'
title: '&lt;future&gt;, énumérations'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 473533d5d22ac5708af7a86cc58a57ac033545af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232133"
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
