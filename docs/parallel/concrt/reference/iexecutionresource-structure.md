---
title: IExecutionResource, structure
ms.date: 11/04/2016
f1_keywords:
- IExecutionResource
- CONCRTRM/concurrency::IExecutionResource
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::CurrentSubscriptionLevel
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetExecutionResourceId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::GetNodeId
- CONCRTRM/concurrency::IExecutionResource::IExecutionResource::Remove
helpviewer_keywords:
- IExecutionResource structure
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
ms.openlocfilehash: 4305948aa4e5da36023c1d4fe8b0b84aa4d59e23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377312"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource, structure

Abstraction d'un thread matériel.

## <a name="syntax"></a>Syntaxe

```cpp
struct IExecutionResource;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IExecutionResource::CurrentSubscriptionLevel](#currentsubscriptionlevel)|Retourne le nombre de racines de processeur virtuel activé et les threads externes souscrits actuellement associés au fil matériel sous-jacent que représente cette ressource d’exécution.|
|[IExecutionResource::GetExecutionResourceId](#getexecutionresourceid)|Retourne un identifiant unique pour le fil matériel que représente cette ressource d’exécution.|
|[IExecutionResource::GetNodeId](#getnodeid)|Renvoie un identifiant unique pour le nœud processeur auquel appartient cette ressource d’exécution.|
|[IExecutionResource::Supprimer](#remove)|Retourne cette ressource d’exécution au gestionnaire des ressources.|

## <a name="remarks"></a>Notes

Les ressources d’exécution peuvent être autonomes ou associées aux racines du processeur virtuel. Une ressource d’exécution autonome est créée lorsqu’un thread de votre application crée un abonnement de thread. Les méthodes [ISchedulerProxy::SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) et [ISchedulerProxy:::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) créer `IExecutionResource` des abonnements de fil, et retourner une interface représentant l’abonnement. La création d’un abonnement de fil est un moyen d’informer le gestionnaire de ressources qu’un thread donné participera au travail en file d’attente à un planificateur, ainsi que le gestionnaire de ressources virtuels racines processeur assigne au planificateur. Le gestionnaire des ressources utilise ces informations pour éviter de sursoumis les threads matériels là où il le peut.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IExecutionResource`

## <a name="requirements"></a>Spécifications

**En-tête:** concrtrm.h

**Namespace:** concurrence

## <a name="iexecutionresourcecurrentsubscriptionlevel-method"></a><a name="currentsubscriptionlevel"></a>IExecutionResource::CurrentSubscriptionLevel Méthode

Retourne le nombre de racines de processeur virtuel activé et les threads externes souscrits actuellement associés au fil matériel sous-jacent que représente cette ressource d’exécution.

```cpp
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Le niveau d’abonnement actuel.

### <a name="remarks"></a>Notes

Le niveau d’abonnement vous indique le nombre de threads en cours d’exécution associés au fil matériel. Cela ne comprend que les fils que le gestionnaire de ressources est au courant sous la forme de threads abonnés, et les racines du processeur virtuel qui exécutent activement des procurations de thread.

Appel de la méthode [ISchedulerProxy::SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread), ou la méthode [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) avec le paramètre `doSubscribeCurrentThread` réglé à la valeur **réelle** incréments le niveau d’abonnement d’un fil matériel par un. Ils retournent `IExecutionResource` également une interface représentant l’abonnement. Un appel correspondant à [l’IExecutionResource: :Supprimer](#remove) décrète le niveau d’abonnement du thread matériel par un.

L’acte d’activer une racine de processeur virtuel en utilisant la méthode [IVirtualProcessorRoot::Activer](ivirtualprocessorroot-structure.md#activate) incréments le niveau d’abonnement d’un fil matériel par un. Les méthodes [IVirtualProcessorRoot::Deactivate](ivirtualprocessorroot-structure.md#deactivate), ou [IExecutionResource::Supprimer](#remove) la décroissance du niveau d’abonnement par un lorsqu’il est invoqué sur une racine de processeur virtuel activé.

Le gestionnaire des ressources utilise l’information sur le niveau d’abonnement comme l’une des façons de déterminer quand déplacer les ressources entre les planificateurs.

## <a name="iexecutionresourcegetexecutionresourceid-method"></a><a name="getexecutionresourceid"></a>IExecutionResource::GetExecutionResourceId Méthode

Retourne un identifiant unique pour le fil matériel que représente cette ressource d’exécution.

```cpp
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Un identifiant unique pour le fil matériel sous-jacent à cette ressource d’exécution.

### <a name="remarks"></a>Notes

Chaque thread matériel se voit attribuer un identifiant unique par le Concurrency Runtime. Si plusieurs ressources d’exécution sont associées au fil matériel, elles auront toutes le même identifiant de ressource d’exécution.

## <a name="iexecutionresourcegetnodeid-method"></a><a name="getnodeid"></a>IExecutionResource::GetNodeId Méthode

Renvoie un identifiant unique pour le nœud processeur auquel appartient cette ressource d’exécution.

```cpp
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Un identifiant unique pour un nœud processeur.

### <a name="remarks"></a>Notes

Le Concurrency Runtime représente des fils matériels sur le système en groupes de nœuds de processeur. Les nœuds sont généralement dérivés de la topologie matérielle du système. Par exemple, tous les processeurs sur une prise spécifique ou un nœud NUMA spécifique peuvent appartenir au même nœud de processeur. Le gestionnaire de ressources attribue des identifiants `0` uniques à `nodeCount - 1`ces `nodeCount` nœuds en commençant par jusqu’à et y compris, où représente le nombre total de nœuds processeur sur le système.

Le nombre de nœuds peut être obtenu à partir de la fonction [GetProcessorNodeCount](concurrency-namespace-functions.md).

## <a name="iexecutionresourceremove-method"></a><a name="remove"></a>IExecutionResource::Supprimer la méthode

Retourne cette ressource d’exécution au gestionnaire des ressources.

```cpp
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>Paramètres

*pScheduler*<br/>
Une interface avec le planificateur qui fait la demande de suppression de cette ressource d’exécution.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour remettre aux ressources d’exécution autonomes ainsi qu’aux ressources d’exécution associées aux racines virtuelles du processeur au gestionnaire de ressources.

S’il s’agit d’une ressource d’exécution autonome que vous avez reçue de l’une ou l’autre des méthodes [ISchedulerProxy::SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread) ou [ISchedulerProxy::RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors), appelant la méthode `Remove` mettra fin à l’abonnement de fil que la ressource a été créée pour représenter. Vous devez mettre fin à tous les abonnements de thread `Remove` avant d’arrêter un proxy de planificateur, et devez appeler à partir du thread qui a créé l’abonnement.

Les racines du processeur virtuel peuvent également être retournées `Remove` au gestionnaire `IVirtualProcessorRoot` des ressources `IExecutionResource` en invoquant la méthode, car l’interface hérite de l’interface. Vous devrez peut-être retourner une racine de processeur virtuel soit en réponse à un appel à la méthode [IScheduler::RemoveVirtualProcessors](ischeduler-structure.md#removevirtualprocessors) méthode, ou lorsque vous avez terminé avec une racine de processeur virtuel sursouscrit que vous avez obtenu de la méthode [ISchedulerProxy::CreateOversubscriber](ischedulerproxy-structure.md#createoversubscriber) méthode. Pour les racines de processeur virtuel, il `Remove` n’y a aucune restriction sur laquelle le thread peut invoquer la méthode.

`invalid_argument`est jeté si `pScheduler` le `NULL`paramètre est réglé à .

`invalid_operation`est jeté si `pScheduler` le paramètre est différent de l’planificateur que cette ressource d’exécution a été créé pour, ou, avec une ressource d’exécution autonome, si le thread actuel est différent du thread qui a créé l’abonnement de fil.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot, structure](ivirtualprocessorroot-structure.md)
