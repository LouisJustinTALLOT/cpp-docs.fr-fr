---
title: task_continuation_context, classe
ms.date: 11/04/2016
f1_keywords:
- task_continuation_context
- PPLTASKS/concurrency::task_continuation_context
- PPLTASKS/concurrency::task_continuation_context::get_current_winrt_context
- PPLTASKS/concurrency::task_continuation_context::use_arbitrary
- PPLTASKS/concurrency::task_continuation_context::use_current
- PPLTASKS/concurrency::task_continuation_context::use_default
- PPLTASKS/concurrency::task_continuation_context::use_synchronous_execution
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
ms.openlocfilehash: ae8ac425f035839cdddc0b19f4f40d3b6369202a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142575"
---
# <a name="task_continuation_context-class"></a>task_continuation_context, classe

La classe `task_continuation_context` vous permet de spécifier où vous souhaitez qu'une continuation soit exécutée. Il est utile d’utiliser cette classe uniquement à partir d’une application Windows Runtime. Pour les applications non-Windows Runtime, le contexte d’exécution de la continuation de tâche est déterminé par le runtime et n’est pas configurable.

## <a name="syntax"></a>Syntaxe

```cpp
class task_continuation_context : public details::_ContextCallback;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[get_current_winrt_context](#get_current_winrt_context)|Retourne un objet de contexte de continuation de tâche qui représente le contexte de thread WinRT actuel.|
|[use_arbitrary](#use_arbitrary)|Crée un contexte de continuation de tâche qui permet au runtime de choisir le contexte d'exécution pour une continuation.|
|[use_current](#use_current)|Renvoie un objet de contexte de continuation de tâche représentant le contexte d'exécution actuel.|
|[use_default](#use_default)|Crée le contexte de continuation de tâche par défaut.|
|[use_synchronous_execution](#use_synchronous_execution)|Retourne un objet de contexte de continuation de tâche qui représente le contexte d’exécution synchrone.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_ContextCallback`

`task_continuation_context`

## <a name="requirements"></a>Spécifications

**En-tête :** ppltasks. h

**Espace de noms :** concurrency

## <a name="get_current_winrt_context"></a>get_current_winrt_context

Retourne un objet de contexte de continuation de tâche qui représente le contexte de thread WinRT actuel.

### <a name="syntax"></a>Syntaxe

```cpp
static task_continuation_context get_current_winrt_context();
```

### <a name="return-value"></a>Valeur de retour

Contexte de thread de Windows Runtime actuel. Retourne une task_continuation_context vide si elle est appelée à partir d’un contexte non Windows Runtime.

### <a name="remarks"></a>Notes

La méthode `get_current_winrt_context` capture le contexte de thread Windows Runtime de l’appelant. Elle retourne un contexte vide aux appelants non-Windows Runtime.

La valeur retournée par `get_current_winrt_context` peut être utilisée pour indiquer au runtime que la continuation doit s’exécuter dans le modèle cloisonné du contexte capturé (STA vs MTA), que la tâche antécédente prenne en charge le cloisonnement ou non. Une tâche qui prend en charge la cloisonnement est une tâche qui désencapsule une Windows Runtime `IAsyncInfo` interface ou une tâche qui est décroisée d’une telle tâche.

Cette méthode est similaire à la méthode `use_current`, mais elle est également disponible pour le C++ code natif C++sans prise en charge de l’extension/CX. Elle est destinée à être utilisée par des utilisateurs C++expérimentés qui écrivent du code de bibliothèque/CX-Agnostic pour les appelants natifs et Windows Runtime. À moins que vous n’ayez besoin de cette fonctionnalité, nous vous recommandons d’utiliser la C++méthode `use_current`, qui est uniquement disponible pour les clients/CX.

## <a name="use_arbitrary"></a>use_arbitrary

Crée un contexte de continuation de tâche qui permet au runtime de choisir le contexte d'exécution pour une continuation.

### <a name="syntax"></a>Syntaxe

```cpp
static task_continuation_context use_arbitrary();
```

### <a name="return-value"></a>Valeur de retour

Contexte de continuation de tâche qui représente un emplacement arbitraire.

### <a name="remarks"></a>Notes

Lorsque ce contexte de continuation est utilisé, la continuation s’exécute dans un contexte que le runtime choisit même si la tâche antécédente est compatible Apartment.

`use_arbitrary` peut être utilisé pour désactiver le comportement par défaut d’une continuation sur une tâche de prise en charge de cloisonnement créée dans un STA.

Cette méthode est uniquement disponible pour les applications Windows Runtime.

## <a name="use_current"></a>use_current

Renvoie un objet de contexte de continuation de tâche représentant le contexte d'exécution actuel.

```cpp
static task_continuation_context use_current();
```

### <a name="return-value"></a>Valeur de retour

Contexte d'exécution actuel.

### <a name="remarks"></a>Notes

Cette méthode capture le contexte de Windows Runtime de l’appelant afin que les continuations puissent être exécutées dans le bon cloisonnement.

La valeur retournée par `use_current` peut être utilisée pour indiquer au runtime que la continuation doit s’exécuter dans le contexte capturé (STA vs MTA), que la tâche antécédente prenne en charge le cloisonnement ou non. Une tâche qui prend en charge la cloisonnement est une tâche qui désencapsule une Windows Runtime `IAsyncInfo` interface ou une tâche qui est décroisée d’une telle tâche.

Cette méthode est uniquement disponible pour les applications Windows Runtime.

## <a name="use_default"></a>use_default

Crée le contexte de continuation de tâche par défaut.

```cpp
static task_continuation_context use_default();
```

### <a name="return-value"></a>Valeur de retour

Contexte de continuation par défaut.

### <a name="remarks"></a>Notes

Le contexte par défaut est utilisé si vous ne spécifiez pas de contexte de continuation lorsque vous appelez la méthode `then`. Dans les applications Windows pour Windows 7 et versions antérieures, ainsi que les applications de bureau sur Windows 8 et versions ultérieures, le runtime détermine l’emplacement d’exécution des continuations de tâches. Toutefois, dans une application Windows Runtime, le contexte de continuation par défaut pour une continuation sur une tâche avec prise en charge de la cloisonnement est le cloisonnement dans lequel `then` est appelé.

Une tâche qui prend en charge la cloisonnement est une tâche qui désencapsule une Windows Runtime `IAsyncInfo` interface ou une tâche qui est décroisée d’une telle tâche. Par conséquent, si vous planifiez une continuation sur une tâche avec prise en charge de cloisonnement dans un Windows Runtime STA, la continuation s’exécutera dans ce STA.

Une continuation sur une tâche qui ne prend pas en charge la cloisonnement s’exécute dans un contexte choisi par le Runtime.

## <a name="use_synchronous_execution"></a>task_continuation_context :: use_synchronous_execution

Retourne un objet de contexte de continuation de tâche qui représente le contexte d’exécution synchrone.

### <a name="syntax"></a>Syntaxe

```cpp
static task_continuation_context use_synchronous_execution();
```

### <a name="return-value"></a>Valeur de retour

Contexte d’exécution synchrone.

### <a name="remarks"></a>Notes

La méthode `use_synchronous_execution` force la tâche de continuation à s’exécuter de façon synchrone sur le contexte, provoquant ainsi l’achèvement de sa tâche antécédente.

Si la tâche antécédente est déjà terminée lorsque la continuation est attachée, la continuation s’exécute de façon synchrone sur le contexte qui attache la continuation.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)
