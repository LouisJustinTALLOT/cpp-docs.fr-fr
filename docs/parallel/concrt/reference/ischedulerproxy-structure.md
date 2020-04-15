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
ms.openlocfilehash: f4a9e79c2da56406610ad6da08fb438e2f92923d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368160"
---
# <a name="ischedulerproxy-structure"></a>ISchedulerProxy, structure

Interface par laquelle les planificateurs communiquent avec le gestionnaire des ressources du runtime d'accès concurrentiel pour négocier l'allocation des ressources.

## <a name="syntax"></a>Syntaxe

```cpp
struct ISchedulerProxy;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[ISchedulerProxy::BindContext](#bindcontext)|Associe un contexte d’exécution à un proxy de thread, s’il n’est pas déjà associé à un.|
|[ISchedulerProxy::CreateOversubscriber](#createoversubscriber)|Crée une nouvelle racine de processeur virtuel sur le fil matériel associé à une ressource d’exécution existante.|
|[ISchedulerProxy::RequestInitialVirtualProcessors](#requestinitialvirtualprocessors)|Demande une allocation initiale des racines de processeur virtuel. Chaque racine de processeur virtuel représente la capacité d’exécuter un thread qui peut effectuer le travail pour le planificateur.|
|[ISchedulerProxy::Shutdown](#shutdown)|Informe le gestionnaire des ressources que le planificateur est en train de fermer. Cela amènera le gestionnaire des ressources à récupérer immédiatement toutes les ressources accordées au planificateur.|
|[ISchedulerProxy::SubscribeCurrentThread](#subscribecurrentthread)|Enregistre le thread actuel auprès du gestionnaire des ressources, l’associant à ce planificateur.|
|[ISchedulerProxy::UnbindContext](#unbindcontext)|Dissocie un proxy de thread du `pContext` contexte d’exécution spécifié par le paramètre et le renvoie à la piscine gratuite de l’usine de proxy de fil. Cette méthode ne peut être appelée que sur un contexte d’exécution qui a été lié via le [ISchedulerProxy::BindContext](#bindcontext) méthode et n’a pas encore été commencé via être le `pContext` paramètre d’un [IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto) méthode appel.|

## <a name="remarks"></a>Notes

Le gestionnaire de `ISchedulerProxy` ressources remet une interface à tous les planificateurs qui s’y enregistre à l’aide de la méthode [IResourceManager::RegisterScheduler](iresourcemanager-structure.md#registerscheduler) méthode.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`ISchedulerProxy`

## <a name="requirements"></a>Spécifications

**En-tête:** concrtrm.h

**Namespace:** concurrence

## <a name="ischedulerproxybindcontext-method"></a><a name="bindcontext"></a>ISchedulerProxy::BindContext Méthode

Associe un contexte d’exécution à un proxy de thread, s’il n’est pas déjà associé à un.

```cpp
virtual void BindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Une interface au contexte d’exécution pour s’associer à un proxy de thread.

### <a name="remarks"></a>Notes

Normalement, la méthode [IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto) liera un proxy de thread à un contexte d’exécution à la demande. Il y a cependant des circonstances où il est nécessaire `SwitchTo` de lier un contexte à l’avance pour s’assurer que la méthode passe à un contexte déjà lié. C’est le cas sur un contexte de planification UMS car il ne peut pas appeler les méthodes qui allouent la mémoire, et la liaison d’un proxy de thread peut impliquer l’allocation de mémoire si un proxy de fil n’est pas facilement disponible dans le pool gratuit de l’usine de proxy de thread.

`invalid_argument`est jeté si `pContext` le `NULL`paramètre a la valeur .

## <a name="ischedulerproxycreateoversubscriber-method"></a><a name="createoversubscriber"></a>ISchedulerProxy::CreateOversubscriber Méthode

Crée une nouvelle racine de processeur virtuel sur le fil matériel associé à une ressource d’exécution existante.

```cpp
virtual IVirtualProcessorRoot* CreateOversubscriber(_Inout_ IExecutionResource* pExecutionResource) = 0;
```

### <a name="parameters"></a>Paramètres

*pExecutionResource*<br/>
Une `IExecutionResource` interface qui représente le fil matériel que vous souhaitez sursoumis.

### <a name="return-value"></a>Valeur de retour

Interface `IVirtualProcessorRoot`.

### <a name="remarks"></a>Notes

Utilisez cette méthode lorsque votre planificateur veut sursoumis un thread matériel particulier pendant un laps de temps limité. Une fois que vous avez terminé avec la racine du processeur [Remove](iexecutionresource-structure.md#remove) virtuel, `IVirtualProcessorRoot` vous devez le retourner au gestionnaire de ressources en appelant la méthode Supprimer sur l’interface.

Vous pouvez même sursabonner une racine `IVirtualProcessorRoot` de processeur virtuel `IExecutionResource` existante, car l’interface hérite de l’interface.

## <a name="ischedulerproxyrequestinitialvirtualprocessors-method"></a><a name="requestinitialvirtualprocessors"></a>ISchedulerProxy::RequestInitialVirtualProcessors Méthode

Demande une allocation initiale des racines de processeur virtuel. Chaque racine de processeur virtuel représente la capacité d’exécuter un thread qui peut effectuer le travail pour le planificateur.

```cpp
virtual IExecutionResource* RequestInitialVirtualProcessors(bool doSubscribeCurrentThread) = 0;
```

### <a name="parameters"></a>Paramètres

*doSubscribeCurrentThread*<br/>
S’il faut souscrire le thread actuel et en tenir compte lors de l’allocation des ressources.

### <a name="return-value"></a>Valeur de retour

L’interface `IExecutionResource` pour le thread `doSubscribeCurrentThread` actuel, si le paramètre a la valeur **vraie**. Si la valeur est **fausse,** la méthode renvoie NULL.

### <a name="remarks"></a>Notes

Avant qu’un planificateur exécute n’importe quel travail, il devrait utiliser cette méthode pour demander des racines de processeur virtuel du gestionnaire de ressource. Le gestionnaire des ressources accédera à la politique du planificateur en utilisant [IScheduler : : GetPolicy](ischeduler-structure.md#getpolicy) et utilisera les valeurs pour les clés `MinConcurrency`de stratégie, `MaxConcurrency` et `TargetOversubscriptionFactor` déterminera le nombre de threads matériels à attribuer au planificateur au départ et le nombre d’racines de processeur virtuel à créer pour chaque thread matériel. Pour plus d’informations sur la façon dont les politiques de planificateur sont utilisées pour déterminer l’allocation initiale d’un planificateur, voir [PolicyElementKey](concurrency-namespace-enums.md).

Le gestionnaire des ressources accorde des ressources à un planificateur en appelant la méthode [IScheduler ::AddVirtualProcessors](ischeduler-structure.md#addvirtualprocessors) avec une liste de racines de processeur virtuel. La méthode est invoquée comme un rappel dans le planificateur avant que cette méthode revient.

Si le planificateur a demandé l’abonnement `doSubscribeCurrentThread` pour le thread actuel `IExecutionResource` en définissant le paramètre à **vrai,** la méthode renvoie une interface. L’abonnement doit être résilié à un moment ultérieur en utilisant la méthode [IExecutionResource::Supprimer la](iexecutionresource-structure.md#remove) méthode.

Lors de la détermination des fils matériels sélectionnés, le gestionnaire de ressources tentera d’optimiser l’affinité des nœuds de processeur. Si l’abonnement est demandé pour le thread actuel, c’est une indication que le thread actuel a l’intention de participer aux travaux assignés à ce planificateur. Dans un tel cas, les racines des processeurs virtuels alloués sont situées sur le nœud processeur sur lequel le thread actuel s’exécute, si possible.

L’acte d’abonner un thread augmente d’un seul le niveau d’abonnement du fil matériel sous-jacent. Le niveau d’abonnement est réduit d’un lorsque l’abonnement est terminé. Pour plus d’informations sur les niveaux d’abonnement, voir [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ischedulerproxyshutdown-method"></a><a name="shutdown"></a>ISchedulerProxy::Méthode d’arrêt

Informe le gestionnaire des ressources que le planificateur est en train de fermer. Cela amènera le gestionnaire des ressources à récupérer immédiatement toutes les ressources accordées au planificateur.

```cpp
virtual void Shutdown() = 0;
```

### <a name="remarks"></a>Notes

Toutes `IExecutionContext` les interfaces que le planificateur a reçues à la `ISchedulerProxy::RequestInitialVirtualProcessors` suite `ISchedulerProxy::SubscribeCurrentThread` de l’abonnement à `IExecutionResource::Remove` un thread externe à l’aide des méthodes ou doivent être retournées au gestionnaire de ressources à l’aide d’un planificateur avant qu’un planificateur ne s’arrête.

Si votre planificateur avait des racines de processeur virtuel désactivé, vous devez les activer à l’aide [d’IVirtualProcessorRoot: ::Activate](ivirtualprocessorroot-structure.md#activate), et avoir les procurations de fil exécutant sur eux laisser la `Dispatch` méthode des contextes d’exécution qu’ils sont l’expédition avant d’invoquer `Shutdown` sur un proxy planificateur.

Il n’est pas nécessaire pour le planificateur de retourner individuellement toutes les racines `Remove` du processeur virtuel que le gestionnaire de ressources lui a accordées par l’intermédiaire d’appels à la méthode parce que toutes les racines des processeurs virtuels seront retournées au gestionnaire des ressources à l’arrêt.

## <a name="ischedulerproxysubscribecurrentthread-method"></a><a name="subscribecurrentthread"></a>ISchedulerProxy::SubscribeCurrentThread Méthode

Enregistre le thread actuel auprès du gestionnaire des ressources, l’associant à ce planificateur.

```cpp
virtual IExecutionResource* SubscribeCurrentThread() = 0;
```

### <a name="return-value"></a>Valeur de retour

L’interfacing `IExecutionResource` représentant le fil actuel dans le runtime.

### <a name="remarks"></a>Notes

Utilisez cette méthode si vous voulez que le gestionnaire de ressources tienne compte du thread actuel tout en allouant des ressources à votre planificateur et à d’autres planificateurs. Il est particulièrement utile lorsque le thread prévoit de participer au travail en file d’attente à votre planificateur, ainsi que les racines du processeur virtuel que le planificateur reçoit du gestionnaire de ressources. Le gestionnaire des ressources utilise des informations pour éviter une sursubscription inutile des fils matériels sur le système.

La ressource d’exécution reçue par cette méthode doit être retournée au gestionnaire de ressources à l’aide de la méthode [IExecutionResource::Supprimer la](iexecutionresource-structure.md#remove) méthode. Le thread qui `Remove` appelle la méthode doit être `SubscribeCurrentThread` le même thread que précédemment appelé la méthode.

L’acte d’abonner un thread augmente d’un seul le niveau d’abonnement du fil matériel sous-jacent. Le niveau d’abonnement est réduit d’un lorsque l’abonnement est terminé. Pour plus d’informations sur les niveaux d’abonnement, voir [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="ischedulerproxyunbindcontext-method"></a><a name="unbindcontext"></a>ISchedulerProxy::Méthode UnbindContext

Dissocie un proxy de thread du `pContext` contexte d’exécution spécifié par le paramètre et le renvoie à la piscine gratuite de l’usine de proxy de fil. Cette méthode ne peut être appelée que sur un contexte d’exécution qui a été lié via le [ISchedulerProxy::BindContext](#bindcontext) méthode et n’a pas encore été commencé via être le `pContext` paramètre d’un [IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto) méthode appel.

```cpp
virtual void UnbindContext(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>Paramètres

*pContext*<br/>
Le contexte d’exécution pour se dissocier de son proxy thread.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[IScheduler, structure](ischeduler-structure.md)<br/>
[IThreadProxy, structure](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot, structure](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager, structure](iresourcemanager-structure.md)
