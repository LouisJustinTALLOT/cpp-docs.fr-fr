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
ms.openlocfilehash: 40799d1ed6e21e6932f1adfbad117c436918b792
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417179"
---
# <a name="iexecutionresource-structure"></a>IExecutionResource, structure

Abstraction d'un thread matériel.

## <a name="syntax"></a>Syntaxe

```cpp
struct IExecutionResource;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[IExecutionResource :: CurrentSubscriptionLevel](#currentsubscriptionlevel)|Retourne le nombre de racines de processeur virtuel activées et de threads externes abonnés actuellement associés au thread matériel sous-jacent représenté par cette ressource d’exécution.|
|[IExecutionResource :: GetExecutionResourceId](#getexecutionresourceid)|Retourne un identificateur unique pour le thread matériel que cette ressource d’exécution représente.|
|[IExecutionResource :: GetNodeId](#getnodeid)|Retourne un identificateur unique pour le nœud de processeur auquel cette ressource d’exécution appartient.|
|[IExecutionResource :: Remove](#remove)|Retourne cette ressource d’exécution au Gestionnaire des ressources.|

## <a name="remarks"></a>Notes

Les ressources d’exécution peuvent être autonomes ou associées à des racines de processeur virtuel. Une ressource d’exécution autonome est créée lorsqu’un thread de votre application crée un abonnement de thread. Les méthodes [ISchedulerProxy :: SubscribeThread](ischedulerproxy-structure.md#subscribecurrentthread) et [ISchedulerProxy :: RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) créent des abonnements de thread, et retournent une interface `IExecutionResource` représentant l’abonnement. La création d’un abonnement de thread est un moyen d’informer le Gestionnaire des ressources qu’un thread donné participera au travail mis en file d’attente dans un planificateur, ainsi que les racines de processeur virtuel Gestionnaire des ressources affectées au planificateur. Le Gestionnaire des ressources utilise les informations pour éviter les threads matériels surabonnant à l’endroit où il peut.

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`IExecutionResource`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrency

## <a name="currentsubscriptionlevel"></a>IExecutionResource :: CurrentSubscriptionLevel, méthode

Retourne le nombre de racines de processeur virtuel activées et de threads externes abonnés actuellement associés au thread matériel sous-jacent représenté par cette ressource d’exécution.

```cpp
virtual unsigned int CurrentSubscriptionLevel() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Niveau d’abonnement actuel.

### <a name="remarks"></a>Notes

Le niveau d’abonnement indique le nombre de threads en cours d’exécution associés au thread matériel. Cela comprend uniquement les threads pris en charge par le Gestionnaire des ressources sous la forme de threads abonnés, et les racines de processeur virtuel qui exécutent activement des proxys de thread.

L’appel de la méthode [ISchedulerProxy :: SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread), ou de la méthode [ISchedulerProxy :: RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors) avec le paramètre `doSubscribeCurrentThread` défini sur la valeur **true** , incrémente le niveau d’abonnement d’un thread matériel d’une unité. Elles retournent également une interface `IExecutionResource` représentant l’abonnement. Un appel correspondant à l' [IExecutionResource :: Remove](#remove) décrémente le niveau d’abonnement du thread matériel d’une unité.

Le fait d’activer une racine de processeur virtuel à l’aide de la méthode [IVirtualProcessorRoot :: Activate](ivirtualprocessorroot-structure.md#activate) incrémente le niveau d’abonnement d’un thread matériel d’une unité. Les méthodes [IVirtualProcessorRoot ::D eactivate](ivirtualprocessorroot-structure.md#deactivate)ou [IExecutionResource :: Remove](#remove) décrément le niveau d’abonnement lorsqu’il est appelé sur une racine de processeur virtuel activée.

L’Gestionnaire des ressources utilise les informations de niveau d’abonnement pour déterminer quand déplacer des ressources entre les planificateurs.

## <a name="getexecutionresourceid"></a>IExecutionResource :: GetExecutionResourceId, méthode

Retourne un identificateur unique pour le thread matériel que cette ressource d’exécution représente.

```cpp
virtual unsigned int GetExecutionResourceId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Identificateur unique pour le thread matériel sous-jacent à cette ressource d’exécution.

### <a name="remarks"></a>Notes

Un identificateur unique est attribué à chaque thread matériel par le runtime d’accès concurrentiel. Si plusieurs ressources d’exécution sont associées à un thread matériel, elles ont toutes le même identificateur de ressource d’exécution.

## <a name="getnodeid"></a>IExecutionResource :: GetNodeId, méthode

Retourne un identificateur unique pour le nœud de processeur auquel cette ressource d’exécution appartient.

```cpp
virtual unsigned int GetNodeId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Identificateur unique pour un nœud de processeur.

### <a name="remarks"></a>Notes

Le runtime d’accès concurrentiel représente les threads matériels sur le système dans des groupes de nœuds de processeur. Les nœuds sont généralement dérivés de la topologie matérielle du système. Par exemple, tous les processeurs sur un socket spécifique ou un nœud NUMA spécifique peuvent appartenir au même nœud de processeur. Le Gestionnaire des ressources assigne des identificateurs uniques à ces nœuds en commençant par `0` jusqu’à `nodeCount - 1`, où `nodeCount` représente le nombre total de nœuds de processeur sur le système.

Le nombre de nœuds peut être obtenu à partir de la fonction [GetProcessorNodeCount,](concurrency-namespace-functions.md).

## <a name="remove"></a>IExecutionResource :: Remove, méthode

Retourne cette ressource d’exécution au Gestionnaire des ressources.

```cpp
virtual void Remove(_Inout_ IScheduler* pScheduler) = 0;
```

### <a name="parameters"></a>Paramètres

*pScheduler*<br/>
Interface au planificateur qui demande la suppression de cette ressource d’exécution.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour retourner des ressources d’exécution autonomes ainsi que des ressources d’exécution associées à des racines de processeur virtuel à la Gestionnaire des ressources.

S’il s’agit d’une ressource d’exécution autonome que vous avez reçue de l’une des méthodes [ISchedulerProxy :: SubscribeCurrentThread](ischedulerproxy-structure.md#subscribecurrentthread) ou [ISchedulerProxy :: RequestInitialVirtualProcessors](ischedulerproxy-structure.md#requestinitialvirtualprocessors), l’appel de la méthode `Remove` met fin à l’abonnement de thread que la ressource a créé pour représenter. Vous devez mettre fin à tous les abonnements de thread avant d’arrêter un proxy de planificateur et appeler `Remove` à partir du thread qui a créé l’abonnement.

Les racines de processeur virtuel, également, peuvent être retournées au Gestionnaire des ressources en appelant la méthode `Remove`, car l’interface `IVirtualProcessorRoot` hérite de l’interface `IExecutionResource`. Vous devrez peut-être retourner une racine de processeur virtuel soit en réponse à un appel à la méthode [iScheduler :: RemoveVirtualProcessors](ischeduler-structure.md#removevirtualprocessors) , soit lorsque vous avez terminé avec une racine de processeur virtuel surabonnée que vous avez obtenue à partir de la méthode [ISchedulerProxy :: CreateOversubscriber](ischedulerproxy-structure.md#createoversubscriber) . Pour les racines de processeur virtuel, il n’existe aucune restriction sur le thread qui peut appeler la méthode `Remove`.

`invalid_argument` est levée si le paramètre `pScheduler` a la valeur `NULL`.

`invalid_operation` est levée si le paramètre `pScheduler` est différent du planificateur pour lequel cette ressource d’exécution a été créée, ou avec une ressource d’exécution autonome, si le thread actuel est différent du thread qui a créé l’abonnement de thread.

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[IVirtualProcessorRoot, structure](ivirtualprocessorroot-structure.md)
