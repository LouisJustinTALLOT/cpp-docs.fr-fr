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
ms.openlocfilehash: fc2fb2df06225a5c963fe39178c1b4a10f77953d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368129"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy, structure

Abstraction d'un thread d'exécution. Selon la clé de stratégie `SchedulerType` du planificateur que vous créez, le gestionnaire des ressources vous accorde un proxy de thread assorti d'un thread Win32 standard ou d'un thread UMS (User-Mode Scheduling). Les threads UMS sont pris en charge sur les systèmes d'exploitation 64 bits avec Windows 7 et ses versions ultérieures.

## <a name="syntax"></a>Syntaxe

```cpp
struct IThreadProxy;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IThreadProxy::GetId](#getid)|Retourne un identifiant unique pour le proxy de thread.|
|[IThreadProxy::SwitchOut](#switchout)|Dissocie le contexte de la racine sous-jacente du processeur virtuel.|
|[IThreadProxy::SwitchTo](#switchto)|Effectue un changement de contexte coopératif du contexte actuel d’exécution à un autre.|
|[IThreadProxy::YieldToSystem](#yieldtosystem)|Oblige le thread appelant à céder l'exécution à un autre thread prêt à s'exécuter sur le processeur actuel. Le système d’exploitation sélectionne le thread suivant à exécuter.|

## <a name="remarks"></a>Notes

Les procurations de fil sont couplées aux `IExecutionContext` contextes d’exécution représentés par l’interface comme moyen d’expédition du travail.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IThreadProxy`

## <a name="requirements"></a>Spécifications

**En-tête:** concrtrm.h

**Namespace:** concurrence

## <a name="ithreadproxygetid-method"></a><a name="getid"></a>IThreadProxy::Méthode GetId

Retourne un identifiant unique pour le proxy de thread.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Un identificateur integer unique.

## <a name="ithreadproxyswitchout-method"></a><a name="switchout"></a>IThreadProxy::Méthode SwitchOut

Dissocie le contexte de la racine sous-jacente du processeur virtuel.

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>Paramètres

*commutateurState*<br/>
Indique l’état du proxy de thread qui exécute l’interrupteur. Le paramètre `SwitchingProxyState`est de type .

### <a name="remarks"></a>Notes

Utilisez `SwitchOut` si vous devez dissocier un contexte de la racine du processeur virtuel sur laquelle il s'exécute, quelle que soit la raison. Selon la valeur que vous passez dans le paramètre `switchState`, et peu importe s'il s'exécute ou non sur une racine du processeur virtuel, l'appel retourne immédiatement ou bloque le proxy de thread associé au contexte. C'est une erreur que d'appeler `SwitchOut` avec le jeu de paramètres défini sur `Idle`. Cela se traduira par une [invalid_argument](../../../standard-library/invalid-argument-class.md) exception.

`SwitchOut` est utile lorsque vous souhaitez réduire le nombre de racines de processeur virtuel de votre planificateur, soit parce que le Gestionnaire des ressources vous a demandé de le faire, soit parce que vous avez demandé une racine de processeur virtuel sursouscrite temporaire et que vous n'en avez plus besoin. Dans ce cas, vous devez invoquer la méthode [IVirtualProcessorRoot::Supprimer](iexecutionresource-structure.md#remove) sur la racine du processeur virtuel, avant de faire un appel à `SwitchOut` avec le paramètre `switchState` réglé à `Blocking`. Cela bloquera le proxy de thread et il reprendra l'exécution lorsqu'une racine de processeur virtuel différente dans le planificateur sera disponible pour l'exécuter. Le proxy de thread de blocage `SwitchTo` peut être repris en appelant la fonction pour passer au contexte d’exécution de ce proxy de fil. Vous pouvez également reprendre le proxy de thread, en utilisant son contexte associé pour activer une racine de processeur virtuel. Pour plus d’informations sur la façon de le faire, voir [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).

`SwitchOut` peut également être utilisé lorsque vous souhaitez réinitialiser le processeur virtuel afin qu'il puisse être activé à l'avenir en bloquant le proxy de thread ou en le détachant temporairement de la racine du processeur virtuel sur lequel il s'exécute, et du planificateur pour lequel il distribue le travail. Utilisez `SwitchOut` avec le paramètre `switchState` défini sur la valeur `Blocking` si vous voulez bloquer le proxy de thread. Il peut ensuite être redémarré en utilisant `SwitchTo` ou `IVirtualProcessorRoot::Activate` comme mentionné ci-dessus. Utilisez `SwitchOut` avec le jeu de paramètres défini sur `Nesting` lorsque vous souhaitez détacher temporairement ce proxy de thread de la racine de processeur virtuel sur lequel il s'exécute, et du planificateur auquel le processeur virtuel est associé. Appeler `SwitchOut` avec le paramètre `switchState` défini sur `Nesting` pendant son exécution sur une racine du processeur virtuel entraînera la réinitialisation de la racine, et le proxy du thread actuel continuera à s'exécuter sans nécessiter de racine. Le proxy de thread est considéré comme ayant quitté le planificateur jusqu’à ce `Blocking` qu’il appelle le [IThreadProxy::SwitchOut](#switchout) méthode avec à un point ultérieur dans le temps. Le deuxième appel à `SwitchOut` avec le jeu de paramètres défini sur `Blocking` est conçu pour retourner le contexte vers un état bloqué afin qu'il puisse être repris par `SwitchTo` ou `IVirtualProcessorRoot::Activate` dans le planificateur dont il est détaché. Comme il ne s'exécutait pas sur une racine du processeur virtuel, aucune réinitialisation n'est effectuée.

Une racine de processeur virtuel réinitialisée n'est aucunement différente d'une racine de processeur virtuel toute neuve qui a été accordée à votre planificateur par le gestionnaire de ressources. Vous pouvez l'utiliser pour exécution en l'activant avec un contexte d'exécution en utilisant `IVirtualProcessorRoot::Activate`.

`SwitchOut`doit être appelé `IThreadProxy` sur l’interface qui représente le thread actuellement exécutant ou les résultats sont indéfinis.

Dans les bibliothèques et les en-têtes fournis avec Visual Studio 2010, cette méthode ne prenait pas de paramètre et ne réinitialisait pas la racine du processeur virtuel. Pour conserver l'ancien comportement, la valeur de paramètre par défaut de `Blocking` est fournie.

## <a name="ithreadproxyswitchto-method"></a><a name="switchto"></a>IThreadProxy::SwitchTo Méthode

Effectue un changement de contexte coopératif du contexte actuel d’exécution à un autre.

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Le contexte d’exécution pour passer en collaboration.

*commutateurState*<br/>
Indique l’état du proxy de thread qui exécute l’interrupteur. Le paramètre `SwitchingProxyState`est de type .

### <a name="remarks"></a>Notes

Utilisez cette méthode pour passer d’un contexte d’exécution à l’autre, de la méthode [IExecutionContext::Dispatch](iexecutioncontext-structure.md#dispatch) du premier contexte d’exécution. La méthode associe `pContext` le contexte d’exécution à un proxy de thread s’il n’est pas déjà associé à un. La propriété du proxy de thread actuel est `switchState` déterminée par la valeur que vous spécifiez pour l’argument.

Utilisez la `Idle` valeur lorsque vous souhaitez retourner le proxy de thread exécutant actuellement au gestionnaire de ressources. `SwitchTo` L’appel `switchState` avec `Idle` le paramètre `pContext` défini pour provoquer le contexte d’exécution de commencer à exécuter sur la ressource d’exécution sous-jacente. La propriété de ce proxy de thread est transférée au gestionnaire de `Dispatch` ressources, `SwitchTo` et vous devez revenir de la méthode du contexte d’exécution peu de temps après les retours, afin de compléter le transfert. Le contexte d’exécution que le proxy de fil envoyait est dissocié du proxy de thread, et le planificateur est libre de le réutiliser ou de le détruire comme bon lui semble.

Utilisez la `Blocking` valeur lorsque vous voulez que ce proxy thread entre dans un état bloqué. `SwitchTo` L’appel `switchState` avec `Blocking` le paramètre `pContext` défini pour provoquer le contexte d’exécution de commencer à exécuter, et bloquer le proxy de thread actuel jusqu’à ce qu’il soit repris. Le planificateur conserve la propriété du proxy de thread `Blocking` lorsque le proxy de thread est dans l’état. Le proxy de thread de blocage `SwitchTo` peut être repris en appelant la fonction pour passer au contexte d’exécution de ce proxy de fil. Vous pouvez également reprendre le proxy de thread, en utilisant son contexte associé pour activer une racine de processeur virtuel. Pour plus d’informations sur la façon de le faire, voir [IVirtualProcessorRoot::Activate](ivirtualprocessorroot-structure.md#activate).

Utilisez la `Nesting` valeur lorsque vous voulez détacher temporairement ce proxy de thread de la racine de processeur virtuel, il est en cours d’exécution sur, et le planificateur, il est l’expédition de travail pour. `SwitchTo` L’appel `switchState` avec `Nesting` le paramètre `pContext` défini pour provoquer le contexte d’exécution de commencer à exécuter et le proxy de thread actuel continue également l’exécution sans avoir besoin d’une racine de processeur virtuel. Le proxy de thread est considéré comme ayant quitté le planificateur jusqu’à ce qu’il appelle le [IThreadProxy::SwitchOut](#switchout) méthode à un moment ultérieur dans le temps. La `IThreadProxy::SwitchOut` méthode pourrait bloquer le proxy de thread jusqu’à ce qu’une racine de processeur virtuel soit disponible pour le reprogrammer.

`SwitchTo`doit être appelé `IThreadProxy` sur l’interface qui représente le thread actuellement exécutant ou les résultats sont indéfinis. La fonction `invalid_argument` jette si `pContext` le `NULL`paramètre est réglé à .

## <a name="ithreadproxyyieldtosystem-method"></a><a name="yieldtosystem"></a>IThreadProxy::YieldToSystem Méthode

Oblige le thread appelant à céder l'exécution à un autre thread prêt à s'exécuter sur le processeur actuel. Le système d’exploitation sélectionne le thread suivant à exécuter.

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>Notes

Lorsqu’il est appelé par un proxy `YieldToSystem` de thread soutenu `SwitchToThread`par un thread Windows régulier, se comporte exactement comme la fonction Windows . Toutefois, lorsqu’on appelle à partir de threads schedulables en mode utilisateur (UMS), la `SwitchToThread` fonction délègue la tâche de choisir le thread suivant pour s’exécuter vers le planificateur de mode utilisateur, et non le système d’exploitation. Pour atteindre l’effet désiré de passer à un `YieldToSystem`thread prêt différent dans le système, utilisez .

`YieldToSystem`doit être appelé `IThreadProxy` sur l’interface qui représente le thread actuellement exécutant ou les résultats sont indéfinis.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[IExecutionContext, structure](iexecutioncontext-structure.md)<br/>
[IScheduler, structure](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot, structure](ivirtualprocessorroot-structure.md)
