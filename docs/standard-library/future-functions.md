---
title: '&lt;future&gt;, fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- future/std::async
- future/std::future_category
- future/std::make_error_code
- future/std::make_error_condition
- future/std::swap
ms.assetid: 1e3acc1e-736a-42dc-ade2-b2fe69aa96bc
helpviewer_keywords:
- std::async [C++]
- std::future_category [C++]
- std::make_error_code [C++]
- std::make_error_condition [C++]
- std::swap [C++]
ms.openlocfilehash: 9b4a8b148dc8b72c7dcc1931802c503be783e9ea
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108601"
---
# <a name="ltfuturegt-functions"></a>&lt;future&gt;, fonctions

||||
|-|-|-|
|[async](#async)|[future_category](#future_category)|[make_error_code](#make_error_code)|
|[make_error_condition](#make_error_condition)|[swap](#swap)|

## <a name="async"></a>  async

Représente un *fournisseur asynchrone*.

```cpp
template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(Fn&& fn, ArgTypes&&... args);

template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(launch policy, Fn&& fn, ArgTypes&&... args);
```

### <a name="parameters"></a>Paramètres

*stratégie*<br/>
Valeur [launch](../standard-library/future-enums.md#launch).

### <a name="remarks"></a>Notes

Définitions des abréviations :

|||
|-|-|
|*dfn*|Résultat de l’appel de `decay_copy(forward<Fn>(fn))`.|
|*dargs*|Résultats des appels `decay_copy(forward<ArgsTypes>(args...))`.|
|*Ty*|Le type `result_of<Fn(ArgTypes...)>::type`.|

La première fonction de modèle retourne `async(launch::any, fn, args...)`.

La deuxième fonction retourne un objet `future<Ty>` dont l’*état asynchrone associé* contient un résultat en plus des valeurs de *dfn* et *dargs* et d’un objet de thread pour gérer un thread d’exécution séparé.

À moins que `decay<Fn>::type` ne soit un type autre que launch, la deuxième fonction ne participe pas à la résolution de surcharge.

La norme C++ stipule que si la stratégie est launch::async, la fonction crée un nouveau thread. Toutefois l’implémentation Microsoft est actuellement non conforme. Il obtient ses threads du ThreadPool Windows, qui, dans certains cas, peut fournir un thread recyclé au lieu d’un nouveau. Cela signifie que le `launch::async` stratégie est réellement implémentée en tant que `launch::async|launch::deferred`.  Une autre implication de l’implémentation basée sur le pool de threads est qu’il n’existe aucune garantie que les variables locales de thread seront détruits lorsque le thread soit terminé. Si le thread est recyclé et fourni à un nouvel appel à `async`, les variables ancien existe toujours. Il est donc recommandé de ne pas utiliser les variables locales de thread avec `async`.

Si *stratégie* est `launch::deferred`, la fonction marque son état asynchrone associé comme contenant un *fonction différée* et retourne. Le premier appel à toute fonction non chronométrée qui attend que l’état asynchrone associé soit prêt appelle la fonction différée en évaluant `INVOKE(dfn, dargs..., Ty)`.

Dans tous les cas, l’état asynchrone associé de l’objet `future` n’est pas défini sur *prêt* avant la fin de l’évaluation de `INVOKE(dfn, dargs..., Ty)`, en levant une exception ou en retournant normalement une valeur. Le résultat de l’état asynchrone associé est une exception, s’il en a été levée une, ou toute valeur retournée par l’évaluation.

> [!NOTE]
> Pour un `future` (ou le dernier [shared_future](../standard-library/shared-future-class.md)) attaché à une tâche démarrée avec `std::async`, le destructeur se bloque si la tâche n’est pas terminée ; autrement dit, il se bloque si ce thread n’a pas encore appelé `.get()` ou `.wait()` et que la tâche est encore en cours d’exécution. Si un `future` obtenu à partir de `std::async` est déplacé en dehors de la portée locale, un autre code qui l’utilise doit être conscient que son destructeur peut empêcher l’état partagé d’être prêt.

La pseudo-fonction `INVOKE` est définie dans [\<functional>](../standard-library/functional.md).

## <a name="future_category"></a>  future_category

Retourne une référence à l’objet [error_category](../standard-library/error-category-class.md) qui caractérise les erreurs associées aux objets `future`.

```cpp
const error_category& future_category() noexcept;
```

## <a name="make_error_code"></a>  make_error_code

Crée un [error_code](../standard-library/error-code-class.md) avec l’objet [error_category](../standard-library/error-category-class.md) qui caractérise les erreurs de [future](../standard-library/future-class.md).

```cpp
inline error_code make_error_code(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Paramètres

*errno*<br/>
Valeur [future_errc](../standard-library/future-enums.md#future_errc) qui identifie l’erreur signalée.

### <a name="return-value"></a>Valeur de retour

`error_code(static_cast<int>(Errno), future_category());`

## <a name="make_error_condition"></a>  make_error_condition

Crée un [error_condition](../standard-library/error-condition-class.md) avec l’objet [error_category](../standard-library/error-category-class.md) qui caractérise les erreurs de [future](../standard-library/future-class.md).

```cpp
inline error_condition make_error_condition(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Paramètres

*errno*<br/>
Valeur [future_errc](../standard-library/future-enums.md#future_errc) qui identifie l’erreur signalée.

### <a name="return-value"></a>Valeur de retour

`error_condition(static_cast<int>(Errno), future_category());`

## <a name="swap"></a>  swap

Échange l’*état asynchrone associé* d’un objet `promise` avec celui d’un autre.

```cpp
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```

### <a name="parameters"></a>Paramètres

*Gauche*<br/>
Objet gauche `promise`.

*Droite*<br/>
Objet droit `promise`.

## <a name="see-also"></a>Voir aussi

[\<future>](../standard-library/future.md)<br/>
