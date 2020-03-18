---
title: ISchedulerProxy, structure
ms.date: 11/04/2016
f1_keywords:
- ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::BindContext
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::CreateOversubscriber
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::RequestInitialVirtualProcessors
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::Shutdown
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::SubscribeCurrentThread
- CONCRTRM/concurrency::ISchedulerProxy::ISchedulerProxy::UnbindContext
helpviewer_keywords:
- ISchedulerProxy structure
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
ms.openlocfilehash: 776f70f9b93eb2e38151ceb5e84b4664420cf954
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419146"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy, structure

Interface par laquelle les planificateurs communiquent avec le gestionnaire des ressources du runtime d'accès concurrentiel pour négocier l'allocation des ressources.

## <a name="syntax"></a>Syntaxe

```cpp
struct ISchedulerProxy;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[ISchedulerProxy :: BindContext](#bindcontext)|Associe un contexte d’exécution à un proxy de thread, s’il n’est pas déjà associé à un.|
|[ISchedulerProxy :: CreateOversubscriber](#createoversubscriber)|Crée une racine de processeur virtuel sur le thread matériel associé à une ressource d’exécution existante.|
|[ISchedulerProxy :: RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|Demande une allocation initiale de racines de processeur virtuel. Chaque racine de processeur virtuel représente la capacité à exécuter un thread capable d’effectuer le travail pour le planificateur.|
|[ISchedulerProxy :: Shutdown](#shutdown)|Avertit le Gestionnaire des ressources que le planificateur s’arrête. Ainsi, l’Gestionnaire des ressources récupère immédiatement toutes les ressources accordées au planificateur.|
|[ISchedulerProxy :: SubscribeCurrentThread](#subscribecurrentthread)|Inscrit le thread actuel avec le Gestionnaire des ressources, en l’associant à ce planificateur.|
|[ISchedulerProxy :: UnbindContext](#unbindcontext)|Dissocie un proxy de thread du contexte d’exécution spécifié par le paramètre `pContext` et le retourne au pool Free du proxy de thread. Cette méthode peut uniquement être appelée dans un contexte d’exécution qui a été lié via la méthode [ISchedulerProxy :: BindContext](#bindcontext) et qui n’a pas encore été démarré par le biais du paramètre `pContext` d’un appel de méthode [IThreadProxy :: SwitchTo](ithreadproxy-structure.md#switchto) .|

## <a name="remarks"></a>Notes

Le Gestionnaire des ressources mains d’une interface `ISchedulerProxy` pour chaque planificateur qui s’inscrit auprès de celui-ci à l’aide de la méthode [IResourceManager :: RegisterScheduler](iresourcemanager-structure.md#registerscheduler) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`ISchedulerProxy`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrency

## <a name="bindcontext"></a>ISchedulerProxy :: BindContext, méthode

Associe un contexte d’exécution à un proxy de thread, s’il n’est pas déjà associé à un.

```cpp
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Interface du contexte d’exécution à associer à un proxy de thread.

### <a name="remarks"></a>Notes

Normalement, la méthode [IThreadProxy :: SwitchTo](ithreadproxy-structure.md#switchto) lie un proxy de thread à un contexte d’exécution à la demande. Toutefois, il existe des circonstances dans lesquelles il est nécessaire de lier un contexte à l’avance pour s’assurer que la méthode `SwitchTo` bascule vers un contexte déjà lié. C’est le cas dans un contexte de planification UMS, car il ne peut pas appeler de méthodes qui allouent de la mémoire, et la liaison d’un proxy de thread peut impliquer l’allocation de mémoire si un proxy de thread n’est pas disponible dans le pool libre de la fabrique de proxy de thread.

`invalid_argument` est levée si le paramètre `pContext` a la valeur `NULL`.

## <a name="createoversubscriber"></a>ISchedulerProxy :: CreateOversubscriber, méthode

Crée une racine de processeur virtuel sur le thread matériel associé à une ressource d’exécution existante.

```cpp
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>Paramètres

*pExecutionResource*<br/>
Interface `IExecutionResource` qui représente le thread matériel que vous souhaitez surabonner.

### <a name="return-value"></a>Valeur de retour

Interface `IVirtualProcessorRoot`.

### <a name="remarks"></a>Notes

Utilisez cette méthode lorsque votre planificateur souhaite surabonner un thread matériel particulier pendant un laps de temps limité. Une fois que vous avez terminé avec la racine du processeur virtuel, vous devez la retourner au gestionnaire de ressources en appelant la méthode [Remove](iexecutionresource-structure.md#remove) sur l’interface `IVirtualProcessorRoot`.

Vous pouvez même surabonner une racine de processeur virtuel existante, car l’interface `IVirtualProcessorRoot` hérite de l’interface `IExecutionResource`.

## <a name="requestinitialvirtualprocessors"></a>ISchedulerProxy :: RequestInitialVirtualProcessors, méthode

Demande une allocation initiale de racines de processeur virtuel. Chaque racine de processeur virtuel représente la capacité à exécuter un thread capable d’effectuer le travail pour le planificateur.

```cpp
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>Paramètres

*doSubscribeCurrentThread*<br/>
Indique s’il faut ou non abonner le thread actuel et le compte lors de l’allocation des ressources.

### <a name="return-value"></a>Valeur de retour

Interface `IExecutionResource` pour le thread actuel, si le paramètre `doSubscribeCurrentThread` a la valeur **true**. Si la valeur est **false**, la méthode retourne la valeur null.

### <a name="remarks"></a>Notes

Avant qu’un planificateur exécute un travail, il doit utiliser cette méthode pour demander des racines de processeur virtuel à partir du Gestionnaire des ressources. Le Gestionnaire des ressources accédera à la stratégie du planificateur à l’aide de [iScheduler :: GetPolicy](ischeduler-structure.md#getpolicy) et utilisera les valeurs des clés de stratégie `MinConcurrency`, `MaxConcurrency` et `TargetOversubscriptionFactor` pour déterminer le nombre de threads matériels à assigner au planificateur initialement et le nombre de racines de processeur virtuel à créer pour chaque thread matériel. Pour plus d’informations sur l’utilisation des stratégies de planificateur pour déterminer l’allocation initiale d’un planificateur, consultez [PolicyElementKey,](concurrency-namespace-enums.md).

Le Gestionnaire des ressources accorde des ressources à un planificateur en appelant la méthode [iScheduler :: AddVirtualProcessors](ischeduler-structure.md#addvirtualprocessors) avec une liste de racines de processeur virtuel. La méthode est appelée comme un rappel dans le planificateur avant le retour de cette méthode.

Si le planificateur a demandé l’abonnement pour le thread actuel en affectant au paramètre `doSubscribeCurrentThread` la **valeur true**, la méthode retourne une interface `IExecutionResource`. L’abonnement doit être terminé ultérieurement à l’aide de la méthode [IExecutionResource :: Remove](iexecutionresource-structure.md#remove) .

Lorsque vous déterminez les threads matériels sélectionnés, le Gestionnaire des ressources tente d’optimiser l’affinité de nœud de processeur. Si un abonnement est demandé pour le thread actuel, il indique que le thread actuel envisage de participer au travail affecté à ce planificateur. Dans ce cas, les racines des processeurs virtuels alloués se trouvent sur le nœud de processeur sur lequel s’exécute le thread actuel, si possible.

L’acte d’abonnement d’un thread augmente d’une unité le niveau d’abonnement du thread matériel sous-jacent. Le niveau d’abonnement est réduit d’une unité lorsque l’abonnement est terminé. Pour plus d’informations sur les niveaux d’abonnement, consultez [IExecutionResource :: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="shutdown"></a>ISchedulerProxy :: Shutdown, méthode

Avertit le Gestionnaire des ressources que le planificateur s’arrête. Ainsi, l’Gestionnaire des ressources récupère immédiatement toutes les ressources accordées au planificateur.

```cpp
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>Notes

Toutes les interfaces de `IExecutionContext` que le planificateur a reçues à la suite de l’abonnement à un thread externe à l’aide des méthodes `ISchedulerProxy::RequestInitialVirtualProcessors` ou `ISchedulerProxy::SubscribeCurrentThread` doivent être retournées au Gestionnaire des ressources à l’aide de `IExecutionResource::Remove` avant qu’un planificateur s’arrête.

Si votre planificateur avait des racines de processeur virtuel désactivées, vous devez les activer à l’aide de [IVirtualProcessorRoot :: Activate](ivirtualprocessorroot-structure.md#activate), et les proxys de thread s’exécutant sur ceux-ci laissent la méthode `Dispatch` des contextes d’exécution qu’ils distribuent avant d’appeler `Shutdown` sur un proxy Scheduler.

Il n’est pas nécessaire que le planificateur retourne individuellement toutes les racines de processeur virtuel que le Gestionnaire des ressources lui a accordées via des appels à la méthode `Remove`, car toutes les racines de processeur virtuel sont retournées à l’Gestionnaire des ressources lors de l’arrêt.

## <a name="subscribecurrentthread"></a>ISchedulerProxy :: SubscribeCurrentThread, méthode

Inscrit le thread actuel avec le Gestionnaire des ressources, en l’associant à ce planificateur.

```cpp
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>Valeur de retour

`IExecutionResource` qui représente le thread actuel dans le Runtime.

### <a name="remarks"></a>Notes

Utilisez cette méthode si vous souhaitez que le Gestionnaire des ressources compte pour le thread actuel lors de l’allocation de ressources à votre planificateur et à d’autres planificateurs. Elle est particulièrement utile lorsque le thread envisage de participer au travail mis en file d’attente dans votre planificateur, avec les racines de processeur virtuel que le planificateur reçoit de la Gestionnaire des ressources. Le Gestionnaire des ressources utilise des informations pour empêcher un surabonnement inutile de threads matériels sur le système.

La ressource d’exécution reçue via cette méthode doit être retournée à la Gestionnaire des ressources à l’aide de la méthode [IExecutionResource :: Remove](iexecutionresource-structure.md#remove) . Le thread qui appelle la méthode `Remove` doit être le même que celui qui a précédemment appelé la méthode `SubscribeCurrentThread`.

L’acte d’abonnement d’un thread augmente d’une unité le niveau d’abonnement du thread matériel sous-jacent. Le niveau d’abonnement est réduit d’une unité lorsque l’abonnement est terminé. Pour plus d’informations sur les niveaux d’abonnement, consultez [IExecutionResource :: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="unbindcontext"></a>ISchedulerProxy :: UnbindContext, méthode

Dissocie un proxy de thread du contexte d’exécution spécifié par le paramètre `pContext` et le retourne au pool Free du proxy de thread. Cette méthode peut uniquement être appelée dans un contexte d’exécution qui a été lié via la méthode [ISchedulerProxy :: BindContext](#bindcontext) et qui n’a pas encore été démarré par le biais du paramètre `pContext` d’un appel de méthode [IThreadProxy :: SwitchTo](ithreadproxy-structure.md#switchto) .

```cpp
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Contexte d’exécution à dissocier de son proxy de thread.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[IScheduler, structure](ischeduler-structure.md)<br/>
[IThreadProxy, structure](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot, structure](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager, structure](iresourcemanager-structure.md)
