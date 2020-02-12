---
title: IScheduler, structure
ms.date: 11/04/2016
f1_keywords:
- IScheduler
- CONCRTRM/concurrency::IScheduler
- CONCRTRM/concurrency::IScheduler::IScheduler::AddVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::GetId
- CONCRTRM/concurrency::IScheduler::IScheduler::GetPolicy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyBusy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyIdle
- CONCRTRM/concurrency::IScheduler::IScheduler::RemoveVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::Statistics
helpviewer_keywords:
- IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
ms.openlocfilehash: cd7b04b0dc5ca1bc496ce87a6459d00ed5813bf7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142319"
---
# <a name="ischeduler-structure"></a>IScheduler, structure

Interface avec une abstraction d'un planificateur de tâches. Le gestionnaire des ressources du runtime d'accès concurrentiel utilise cette interface pour communiquer avec les planificateurs de tâches.

## <a name="syntax"></a>Syntaxe

```cpp
struct IScheduler;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[IScheduler :: AddVirtualProcessors](#addvirtualprocessors)|Fournit un planificateur avec un ensemble de racines de processeur virtuel pour son utilisation. Chaque `IVirtualProcessorRoot` interface représente le droit d’exécuter un thread unique qui peut effectuer le travail pour le compte du planificateur.|
|[IScheduler :: GetId](#getid)|Retourne un identificateur unique pour le planificateur.|
|[IScheduler :: GetPolicy](#getpolicy)|Retourne une copie de la stratégie du planificateur. Pour plus d’informations sur les stratégies de planificateur, consultez [SchedulerPolicy](schedulerpolicy-class.md).|
|[IScheduler :: NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|Notifie ce planificateur que les threads matériels représentés par l’ensemble de racines de processeur virtuel dans le tableau `ppVirtualProcessorRoots` sont désormais utilisés par d’autres planificateurs.|
|[IScheduler :: NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|Notifie ce planificateur que les threads matériels représentés par l’ensemble de racines de processeur virtuel dans le tableau `ppVirtualProcessorRoots` ne sont pas utilisés par d’autres planificateurs.|
|[IScheduler :: RemoveVirtualProcessors](#removevirtualprocessors)|Lance la suppression des racines de processeur virtuel précédemment allouées à ce planificateur.|
|[IScheduler :: Statistics](#statistics)|Fournit des informations relatives à l’arrivée des tâches et aux taux de saisie semi-automatique, et à la modification de la longueur de la file d’attente pour un planificateur.|

## <a name="remarks"></a>Notes

Si vous implémentez un planificateur personnalisé qui communique avec le Gestionnaire des ressources, vous devez fournir une implémentation de l’interface `IScheduler`. Cette interface est une extrémité d’un canal bidirectionnel de communication entre un planificateur et le Gestionnaire des ressources. L’autre extrémité est représentée par les interfaces `IResourceManager` et `ISchedulerProxy` qui sont implémentées par le Gestionnaire des ressources.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IScheduler`

## <a name="requirements"></a>Spécifications

**En-tête :** concrtrm. h

**Espace de noms :** concurrency

## <a name="addvirtualprocessors"></a>Méthode IScheduler :: AddVirtualProcessors

Fournit un planificateur avec un ensemble de racines de processeur virtuel pour son utilisation. Chaque `IVirtualProcessorRoot` interface représente le droit d’exécuter un thread unique qui peut effectuer le travail pour le compte du planificateur.

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Paramètres

*ppVirtualProcessorRoots*<br/>
Tableau d’interfaces `IVirtualProcessorRoot` représentant les racines de processeur virtuel ajoutées au planificateur.

*count*<br/>
Nombre d’interfaces de `IVirtualProcessorRoot` dans le tableau.

### <a name="remarks"></a>Notes

L’Gestionnaire des ressources appelle la méthode `AddVirtualProcessor` pour accorder un ensemble initial de racines de processeur virtuel à un planificateur. Il peut également appeler la méthode pour ajouter des racines de processeur virtuel au planificateur lorsqu’il rééquilibre les ressources entre les planificateurs.

## <a name="getid"></a>IScheduler :: GetId, méthode

Retourne un identificateur unique pour le planificateur.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Identificateur entier unique.

### <a name="remarks"></a>Notes

Vous devez utiliser la fonction [GetSchedulerId,](concurrency-namespace-functions.md) pour obtenir un identificateur unique pour l’objet qui implémente l’interface `IScheduler`, avant d’utiliser l’interface en tant que paramètre pour les méthodes fournies par l’gestionnaire des ressources. Vous êtes censé retourner le même identificateur lorsque la fonction `GetId` est appelée.

Un identificateur obtenu à partir d’une source différente peut entraîner un comportement indéfini.

## <a name="getpolicy"></a>IScheduler :: GetPolicy, méthode

Retourne une copie de la stratégie du planificateur. Pour plus d’informations sur les stratégies de planificateur, consultez [SchedulerPolicy](schedulerpolicy-class.md).

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Copie de la stratégie du planificateur.

## <a name="notifyresourcesexternallybusy"></a>Méthode IScheduler :: NotifyResourcesExternallyBusy

Notifie ce planificateur que les threads matériels représentés par l’ensemble de racines de processeur virtuel dans le tableau `ppVirtualProcessorRoots` sont désormais utilisés par d’autres planificateurs.

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Paramètres

*ppVirtualProcessorRoots*<br/>
Tableau d' `IVirtualProcessorRoot` interfaces associées aux threads matériels sur lesquels d’autres planificateurs sont devenus occupés.

*count*<br/>
Nombre d’interfaces de `IVirtualProcessorRoot` dans le tableau.

### <a name="remarks"></a>Notes

Il est possible qu’un thread matériel particulier soit affecté à plusieurs planificateurs à la fois. Cela peut être dû au fait qu’il n’y a pas assez de threads matériels sur le système pour satisfaire à la concurrence minimale pour tous les planificateurs, sans partager les ressources. Il est également possible que les ressources soient temporairement affectées à d’autres planificateurs lorsque le planificateur propriétaire ne les utilise pas, par le biais de toutes ses racines de processeur virtuel sur ce thread matériel qui est désactivée.

Le niveau d’abonnement d’un thread matériel est indiqué par le nombre de threads abonnés et les racines de processeur virtuel activées associés à ce thread matériel. Du point de vue d’un planificateur particulier, le niveau d’abonnement externe d’un thread matériel est la partie de l’abonnement auquel les autres planificateurs contribuent. Les notifications que les ressources sont occupées en externe sont envoyées à un planificateur lorsque le niveau d’abonnement externe d’un thread matériel passe de zéro à un secteur positif.

Les notifications via cette méthode sont envoyées uniquement aux planificateurs qui ont une stratégie dans laquelle la valeur de la clé de stratégie `MinConcurrency` est égale à la valeur de la clé de stratégie `MaxConcurrency`. Pour plus d’informations sur les stratégies de planificateur, consultez [SchedulerPolicy](schedulerpolicy-class.md).

Un planificateur qui qualifie les notifications reçoit un ensemble de notifications initiales lorsqu’il est créé, en l’informant que les ressources qu’il vient d’attribuer sont occupées ou inactives en externe.

## <a name="notifyresourcesexternallyidle"></a>Méthode IScheduler :: NotifyResourcesExternallyIdle

Notifie ce planificateur que les threads matériels représentés par l’ensemble de racines de processeur virtuel dans le tableau `ppVirtualProcessorRoots` ne sont pas utilisés par d’autres planificateurs.

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Paramètres

*ppVirtualProcessorRoots*<br/>
Tableau d' `IVirtualProcessorRoot` interfaces associées aux threads matériels sur lesquels d’autres planificateurs sont devenus inactifs.

*count*<br/>
Nombre d’interfaces de `IVirtualProcessorRoot` dans le tableau.

### <a name="remarks"></a>Notes

Il est possible qu’un thread matériel particulier soit affecté à plusieurs planificateurs à la fois. Cela peut être dû au fait qu’il n’y a pas assez de threads matériels sur le système pour satisfaire à la concurrence minimale pour tous les planificateurs, sans partager les ressources. Il est également possible que les ressources soient temporairement affectées à d’autres planificateurs lorsque le planificateur propriétaire ne les utilise pas, par le biais de toutes ses racines de processeur virtuel sur ce thread matériel qui est désactivée.

Le niveau d’abonnement d’un thread matériel est indiqué par le nombre de threads abonnés et les racines de processeur virtuel activées associés à ce thread matériel. Du point de vue d’un planificateur particulier, le niveau d’abonnement externe d’un thread matériel est la partie de l’abonnement auquel les autres planificateurs contribuent. Les notifications que les ressources sont occupées en externe sont envoyées à un planificateur lorsque le niveau d’abonnement externe d’un thread matériel est égal à zéro d’une valeur positive précédente.

Les notifications via cette méthode sont envoyées uniquement aux planificateurs qui ont une stratégie dans laquelle la valeur de la clé de stratégie `MinConcurrency` est égale à la valeur de la clé de stratégie `MaxConcurrency`. Pour plus d’informations sur les stratégies de planificateur, consultez [SchedulerPolicy](schedulerpolicy-class.md).

Un planificateur qui qualifie les notifications reçoit un ensemble de notifications initiales lorsqu’il est créé, en l’informant que les ressources qu’il vient d’attribuer sont occupées ou inactives en externe.

## <a name="removevirtualprocessors"></a>Méthode IScheduler :: RemoveVirtualProcessors

Lance la suppression des racines de processeur virtuel précédemment allouées à ce planificateur.

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Paramètres

*ppVirtualProcessorRoots*<br/>
Tableau d’interfaces `IVirtualProcessorRoot` représentant les racines de processeur virtuel à supprimer.

*count*<br/>
Nombre d’interfaces de `IVirtualProcessorRoot` dans le tableau.

### <a name="remarks"></a>Notes

Le Gestionnaire des ressources appelle la méthode `RemoveVirtualProcessors` pour reprendre un ensemble de racines de processeur virtuel d’un planificateur. Le planificateur est supposé appeler la méthode [Remove](iexecutionresource-structure.md#remove) sur chaque interface lorsqu’il est terminé avec les racines de processeur virtuel. N’utilisez pas d’interface `IVirtualProcessorRoot` une fois que vous avez appelé la méthode `Remove`.

Le paramètre `ppVirtualProcessorRoots` pointe vers un tableau d’interfaces. Parmi l’ensemble des racines de processeur virtuel à supprimer, les racines n’ont jamais été activées peuvent être retournées immédiatement à l’aide de la méthode `Remove`. Les racines qui ont été activées et qui exécutent un travail, ou qui ont été désactivées et attendent le travail à arriver, doivent être retournées de façon asynchrone. Le planificateur doit faire chaque tentative de suppression de la racine du processeur virtuel aussi rapidement que possible. Le retardement de la suppression des racines de processeur virtuel peut entraîner un surabonnement non intentionnel dans le planificateur.

## <a name="statistics"></a>IScheduler :: Statistics, méthode

Fournit des informations relatives à l’arrivée des tâches et aux taux de saisie semi-automatique, et à la modification de la longueur de la file d’attente pour un planificateur.

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>Paramètres

*pTaskCompletionRate*<br/>
Nombre de tâches qui ont été effectuées par le planificateur depuis le dernier appel à cette méthode.

*pTaskArrivalRate*<br/>
Nombre de tâches qui sont arrivées dans le planificateur depuis le dernier appel à cette méthode.

*pNumberOfTasksEnqueued*<br/>
Nombre total de tâches dans toutes les files d’attente du planificateur.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’Gestionnaire des ressources afin de collecter des statistiques pour un planificateur. Les statistiques collectées ici seront utilisées pour générer des algorithmes de commentaires dynamiques afin de déterminer à quel moment il convient d’attribuer davantage de ressources au planificateur et de libérer des ressources. Les valeurs fournies par le planificateur peuvent être optimistes et ne doivent pas nécessairement refléter le nombre actuel avec précision.

Vous devez implémenter cette méthode si vous souhaitez que le Gestionnaire des ressources utiliser des commentaires sur des tâches telles que l’arrivée d’une tâche afin de déterminer comment équilibrer les ressources entre votre planificateur et les autres planificateurs inscrits auprès du Gestionnaire des ressources. Si vous choisissez de ne pas regrouper les statistiques, vous pouvez définir la clé de stratégie `DynamicProgressFeedback` sur la valeur `DynamicProgressFeedbackDisabled` dans la stratégie de votre planificateur, et la Gestionnaire des ressources n’appellera pas cette méthode sur votre planificateur.

En l’absence d’informations statistiques, le Gestionnaire des ressources utilisera des niveaux d’abonnement de thread matériel pour prendre des décisions d’allocation et de migration des ressources. Pour plus d’informations sur les niveaux d’abonnement, consultez [IExecutionResource :: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[PolicyElementKey,](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy, classe](schedulerpolicy-class.md)<br/>
[IExecutionContext, structure](iexecutioncontext-structure.md)<br/>
[IThreadProxy, structure](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot, structure](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager, structure](iresourcemanager-structure.md)
