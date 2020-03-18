---
title: IThreadProxy, structure
ms.date: 11/04/2016
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
ms.openlocfilehash: b87694393af4634ec97d05070aa5513cd132098a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417158"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy, structure

Abstraction d'un thread d'exécution. Selon la clé de stratégie `SchedulerType` du planificateur que vous créez, le gestionnaire des ressources vous accorde un proxy de thread assorti d'un thread Win32 standard ou d'un thread UMS (User-Mode Scheduling). Les threads UMS sont pris en charge sur les systèmes d'exploitation 64 bits avec Windows 7 et ses versions ultérieures.

## <a name="syntax"></a>Syntaxe

```cpp
struct IThreadProxy;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[IThreadProxy :: GetId](#getid)|Retourne un identificateur unique pour le proxy de thread.|
|[IThreadProxy :: SwitchOut](#switchout)|Dissocie le contexte de la racine sous-jacente du processeur virtuel.|
|[IThreadProxy :: SwitchTo](#switchto)|Effectue un basculement de contexte coopératif du contexte en cours d’exécution vers un autre.|
|[IThreadProxy :: YieldToSystem](#yieldtosystem)|Oblige le thread appelant à céder l'exécution à un autre thread prêt à s'exécuter sur le processeur actuel. Le système d’exploitation sélectionne le thread suivant à exécuter.|

## <a name="remarks"></a>Notes

Les proxys de thread sont associés aux contextes d’exécution représentés par l’interface `IExecutionContext` comme un moyen de distribuer le travail.

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`IThreadProxy`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrency

## <a name="getid"></a>IThreadProxy :: GetId, méthode

Retourne un identificateur unique pour le proxy de thread.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Identificateur entier unique.

## <a name="switchout"></a>IThreadProxy :: SwitchOut, méthode

Dissocie le contexte de la racine sous-jacente du processeur virtuel.

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>Paramètres

*switchState*<br/>
Indique l’état du proxy de thread qui exécute le commutateur. Le paramètre est de type `SwitchingProxyState`.

### <a name="remarks"></a>Notes

Utilisez `SwitchOut` si vous devez dissocier un contexte de la racine du processeur virtuel sur laquelle il s'exécute, quelle que soit la raison. Selon la valeur que vous passez dans le paramètre `switchState`, et peu importe s'il s'exécute ou non sur une racine du processeur virtuel, l'appel retourne immédiatement ou bloque le proxy de thread associé au contexte. C'est une erreur que d'appeler `SwitchOut` avec le jeu de paramètres défini sur `Idle`. Cela entraînera une exception [invalid_argument](../../../standard-library/invalid-argument-class.md) .

`SwitchOut` est utile lorsque vous souhaitez réduire le nombre de racines de processeur virtuel de votre planificateur, soit parce que le Gestionnaire des ressources vous a demandé de le faire, soit parce que vous avez demandé une racine de processeur virtuel sursouscrite temporaire et que vous n'en avez plus besoin. Dans ce cas, vous devez appeler la méthode [IVirtualProcessorRoot :: Remove](iexecutionresource-structure.md#remove) sur la racine du processeur virtuel, avant d’effectuer un appel à `SwitchOut` avec le paramètre `switchState` défini sur `Blocking`. Cela bloquera le proxy de thread et il reprendra l'exécution lorsqu'une racine de processeur virtuel différente dans le planificateur sera disponible pour l'exécuter. Le proxy de thread bloquant peut être repris en appelant la fonction `SwitchTo` pour basculer vers le contexte d’exécution de ce proxy de thread. Vous pouvez également reprendre le proxy de thread en utilisant son contexte associé pour activer une racine de processeur virtuel. Pour plus d’informations sur la façon de procéder, consultez [IVirtualProcessorRoot :: Activate](ivirtualprocessorroot-structure.md#activate).

`SwitchOut` peut également être utilisé lorsque vous souhaitez réinitialiser le processeur virtuel afin qu'il puisse être activé à l'avenir en bloquant le proxy de thread ou en le détachant temporairement de la racine du processeur virtuel sur lequel il s'exécute, et du planificateur pour lequel il distribue le travail. Utilisez `SwitchOut` avec le paramètre `switchState` défini sur la valeur `Blocking` si vous voulez bloquer le proxy de thread. Il peut ensuite être redémarré en utilisant `SwitchTo` ou `IVirtualProcessorRoot::Activate` comme mentionné ci-dessus. Utilisez `SwitchOut` avec le jeu de paramètres défini sur `Nesting` lorsque vous souhaitez détacher temporairement ce proxy de thread de la racine de processeur virtuel sur lequel il s'exécute, et du planificateur auquel le processeur virtuel est associé. Appeler `SwitchOut` avec le paramètre `switchState` défini sur `Nesting` pendant son exécution sur une racine du processeur virtuel entraînera la réinitialisation de la racine, et le proxy du thread actuel continuera à s'exécuter sans nécessiter de racine. Le proxy de thread est considéré comme ayant quitté le planificateur jusqu’à ce qu’il appelle la méthode [IThreadProxy :: SwitchOut](#switchout) avec `Blocking` à un moment ultérieur. Le deuxième appel à `SwitchOut` avec le jeu de paramètres défini sur `Blocking` est conçu pour retourner le contexte vers un état bloqué afin qu'il puisse être repris par `SwitchTo` ou `IVirtualProcessorRoot::Activate` dans le planificateur dont il est détaché. Comme il ne s'exécutait pas sur une racine du processeur virtuel, aucune réinitialisation n'est effectuée.

Une racine de processeur virtuel réinitialisée n'est aucunement différente d'une racine de processeur virtuel toute neuve qui a été accordée à votre planificateur par le gestionnaire de ressources. Vous pouvez l'utiliser pour exécution en l'activant avec un contexte d'exécution en utilisant `IVirtualProcessorRoot::Activate`.

`SwitchOut` doit être appelée sur l’interface `IThreadProxy` qui représente le thread en cours d’exécution ou les résultats ne sont pas définis.

Dans les bibliothèques et les en-têtes fournis avec Visual Studio 2010, cette méthode ne prenait pas de paramètre et ne réinitialisait pas la racine du processeur virtuel. Pour conserver l'ancien comportement, la valeur de paramètre par défaut de `Blocking` est fournie.

## <a name="switchto"></a>IThreadProxy :: SwitchTo, méthode

Effectue un basculement de contexte coopératif du contexte en cours d’exécution vers un autre.

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Contexte d’exécution vers lequel basculer de manière coopérative.

*switchState*<br/>
Indique l’état du proxy de thread qui exécute le commutateur. Le paramètre est de type `SwitchingProxyState`.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour passer d’un contexte d’exécution à un autre, à partir de la méthode [IExecutionContext ::D ispatch](iexecutioncontext-structure.md#dispatch) du premier contexte d’exécution. La méthode associe le contexte d’exécution `pContext` à un proxy de thread s’il n’est pas déjà associé à un. La propriété du proxy de thread actuel est déterminée par la valeur que vous spécifiez pour l’argument `switchState`.

Utilisez la valeur `Idle` lorsque vous souhaitez retourner le proxy de thread en cours d’exécution au Gestionnaire des ressources. L’appel de `SwitchTo` avec le paramètre `switchState` défini sur `Idle` entraîne le démarrage de l’exécution du contexte d’exécution `pContext` sur la ressource d’exécution sous-jacente. La propriété de ce proxy de thread est transférée au Gestionnaire des ressources, et vous devez retourner la méthode `Dispatch` du contexte d’exécution peu après que `SwitchTo` retourne, afin d’effectuer le transfert. Le contexte d’exécution de la distribution du proxy de thread est dissocié du proxy de thread, et le planificateur est libre de le réutiliser ou de le détruire à votre convenance.

Utilisez la valeur `Blocking` lorsque vous souhaitez que ce proxy de thread entre dans un État bloqué. L’appel de `SwitchTo` avec le paramètre `switchState` défini sur `Blocking` entraîne le démarrage de l’exécution du contexte d’exécution `pContext` et le blocage du proxy de thread actuel jusqu’à sa reprise. Le planificateur conserve la propriété du proxy de thread lorsque le proxy de thread est dans l’État `Blocking`. Le proxy de thread bloquant peut être repris en appelant la fonction `SwitchTo` pour basculer vers le contexte d’exécution de ce proxy de thread. Vous pouvez également reprendre le proxy de thread en utilisant son contexte associé pour activer une racine de processeur virtuel. Pour plus d’informations sur la façon de procéder, consultez [IVirtualProcessorRoot :: Activate](ivirtualprocessorroot-structure.md#activate).

Utilisez la valeur `Nesting` lorsque vous souhaitez détacher temporairement ce proxy de thread de la racine du processeur virtuel sur lequel il s’exécute, et le planificateur pour lequel il distribue le travail. L’appel de `SwitchTo` avec le paramètre `switchState` défini sur `Nesting` entraîne le démarrage de l’exécution du contexte d’exécution `pContext` et le proxy de thread actuel continue à s’exécuter sans avoir besoin d’une racine de processeur virtuel. Le proxy de thread est considéré comme ayant quitté le planificateur jusqu’à ce qu’il appelle la méthode [IThreadProxy :: SwitchOut](#switchout) à un moment ultérieur. La méthode `IThreadProxy::SwitchOut` peut bloquer le proxy de thread jusqu’à ce qu’une racine de processeur virtuel soit disponible pour le replanifier.

`SwitchTo` doit être appelée sur l’interface `IThreadProxy` qui représente le thread en cours d’exécution ou les résultats ne sont pas définis. La fonction lève `invalid_argument` si le paramètre `pContext` a la valeur `NULL`.

## <a name="yieldtosystem"></a>IThreadProxy :: YieldToSystem, méthode

Oblige le thread appelant à céder l'exécution à un autre thread prêt à s'exécuter sur le processeur actuel. Le système d’exploitation sélectionne le thread suivant à exécuter.

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>Notes

En cas d’appel par un proxy de thread stocké par un thread Windows normal, `YieldToSystem` se comporte exactement comme la fonction Windows `SwitchToThread`. Toutefois, en cas d’appel à partir de threads UMS (user-mode), la fonction `SwitchToThread` délègue la tâche consistant à sélectionner le thread suivant à exécuter sur le planificateur en mode utilisateur, et non sur le système d’exploitation. Pour obtenir l’effet souhaité de basculer vers un autre thread prêt dans le système, utilisez `YieldToSystem`.

`YieldToSystem` doit être appelée sur l’interface `IThreadProxy` qui représente le thread en cours d’exécution ou les résultats ne sont pas définis.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[IExecutionContext, structure](iexecutioncontext-structure.md)<br/>
[IScheduler, structure](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot, structure](ivirtualprocessorroot-structure.md)
