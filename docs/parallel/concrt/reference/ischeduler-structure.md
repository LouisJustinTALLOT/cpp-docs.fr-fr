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
ms.openlocfilehash: ccd82b5c5112bc322717f2b58d79d4c8f34f5bbd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368173"
---
# <a name="ischeduler-structure"></a>IScheduler, structure

Interface avec une abstraction d'un planificateur de tâches. Le gestionnaire des ressources du runtime d'accès concurrentiel utilise cette interface pour communiquer avec les planificateurs de tâches.

## <a name="syntax"></a>Syntaxe

```cpp
struct IScheduler;
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IScheduler::AddVirtualProcessors](#addvirtualprocessors)|Fournit à un planificateur un ensemble de racines de processeur virtuel pour son utilisation. Chaque `IVirtualProcessorRoot` interface représente le droit d’exécuter un seul thread qui peut effectuer le travail pour le compte du planificateur.|
|[IScheduler::GetId](#getid)|Retourne un identifiant unique pour le planificateur.|
|[IScheduler::GetPolicy](#getpolicy)|Retourne une copie de la police du planificateur. Pour plus d’informations sur les politiques de planificateur, voir [SchedulerPolicy](schedulerpolicy-class.md).|
|[IScheduler::NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|Informe ce planificateur que les fils matériels représentés par l’ensemble des racines du processeur virtuel dans le tableau `ppVirtualProcessorRoots` sont maintenant utilisés par d’autres planificateurs.|
|[IScheduler::NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|Informe ce planificateur que les fils matériels représentés par l’ensemble des racines du processeur virtuel dans le tableau `ppVirtualProcessorRoots` ne sont pas utilisés par d’autres planificateurs.|
|[IScheduler::RemoveVirtualProcessors](#removevirtualprocessors)|Initie la suppression des racines de processeur virtuel qui ont été précédemment allouées à ce planificateur.|
|[IScheduler::Statistiques](#statistics)|Fournit de l’information sur les taux d’arrivée et d’achèvement des tâches et des changements dans la longueur des files d’attente pour un planificateur.|

## <a name="remarks"></a>Notes

Si vous implémentez un planificateur personnalisé qui communique avec le gestionnaire `IScheduler` de ressources, vous devez fournir une implémentation de l’interface. Cette interface est l’une des extrémités d’un canal de communication bidirectionnel entre un planificateur et le gestionnaire des ressources. L’autre extrémité est `IResourceManager` représentée `ISchedulerProxy` par les interfaces et les interfaces qui sont mises en œuvre par le gestionnaire des ressources.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IScheduler`

## <a name="requirements"></a>Spécifications

**En-tête:** concrtrm.h

**Namespace:** concurrence

## <a name="ischeduleraddvirtualprocessors-method"></a><a name="addvirtualprocessors"></a>IScheduler::AddVirtualProcessors Méthode

Fournit à un planificateur un ensemble de racines de processeur virtuel pour son utilisation. Chaque `IVirtualProcessorRoot` interface représente le droit d’exécuter un seul thread qui peut effectuer le travail pour le compte du planificateur.

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Paramètres

*ppVirtualProcessorRoots*<br/>
Un éventail `IVirtualProcessorRoot` d’interfaces représentant les racines du processeur virtuel en cours d’ajout au planificateur.

*count*<br/>
Le nombre `IVirtualProcessorRoot` d’interfaces dans le tableau.

### <a name="remarks"></a>Notes

Le gestionnaire des `AddVirtualProcessor` ressources invoque la méthode pour accorder un premier ensemble de racines de processeur virtuel à un planificateur. Il pourrait également invoquer la méthode pour ajouter des racines de processeur virtuel au planificateur quand il rééquilibre les ressources entre les planificateurs.

## <a name="ischedulergetid-method"></a><a name="getid"></a>IScheduler::GetId Méthode

Retourne un identifiant unique pour le planificateur.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Un identificateur integer unique.

### <a name="remarks"></a>Notes

Vous devez utiliser la fonction [GetSchedulerId](concurrency-namespace-functions.md) pour obtenir un `IScheduler` identifiant unique pour l’objet qui implémente l’interface, avant d’utiliser l’interface comme paramètre aux méthodes fournies par le gestionnaire de ressources. On s’attend à ce `GetId` que vous retournons le même identifiant lorsque la fonction est invoquée.

Un identifiant obtenu à partir d’une autre source pourrait entraîner un comportement indéfini.

## <a name="ischedulergetpolicy-method"></a><a name="getpolicy"></a>IScheduler::GetPolicy Méthode

Retourne une copie de la police du planificateur. Pour plus d’informations sur les politiques de planificateur, voir [SchedulerPolicy](schedulerpolicy-class.md).

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Valeur de retour

Une copie de la politique du planificateur.

## <a name="ischedulernotifyresourcesexternallybusy-method"></a><a name="notifyresourcesexternallybusy"></a>IScheduler::NotifyResourcesExternallyBusy Méthode

Informe ce planificateur que les fils matériels représentés par l’ensemble des racines du processeur virtuel dans le tableau `ppVirtualProcessorRoots` sont maintenant utilisés par d’autres planificateurs.

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Paramètres

*ppVirtualProcessorRoots*<br/>
Un éventail `IVirtualProcessorRoot` d’interfaces associées aux fils matériels sur lesquels d’autres planificateurs sont devenus occupés.

*count*<br/>
Le nombre `IVirtualProcessorRoot` d’interfaces dans le tableau.

### <a name="remarks"></a>Notes

Il est possible qu’un thread matériel particulier soit affecté à plusieurs planificateurs en même temps. Une raison à cela pourrait être qu’il n’y a pas assez de fils matériels sur le système pour satisfaire la concurrence minimale pour tous les planificateurs, sans partager les ressources. Une autre possibilité est que les ressources sont temporairement affectées à d’autres planificateurs lorsque le planificateur propriétaire ne les utilise pas, par le moyen de toutes ses racines de processeur virtuel sur ce fil matériel étant désactivé.

Le niveau d’abonnement d’un thread matériel est indiqué par le nombre de threads abonnés et les racines de processeur virtuel activé associées à ce fil matériel. Du point de vue d’un planificateur particulier, le niveau d’abonnement externe d’un thread matériel est la partie de l’abonnement auquel les autres planificateurs contribuent. Les notifications indiquant que les ressources sont occupées à l’extérieur sont envoyées à un planificateur lorsque le niveau d’abonnement externe pour un thread matériel passe de zéro en territoire positif.

Les notifications par cette méthode ne sont envoyées qu’aux planificateurs qui ont une politique où la valeur de la `MinConcurrency` clé de stratégie est égale à la valeur de la `MaxConcurrency` clé de la stratégie. Pour plus d’informations sur les politiques de planificateur, voir [SchedulerPolicy](schedulerpolicy-class.md).

Un planificateur qui est admissible aux notifications reçoit un ensemble de notifications initiales lorsqu’elle est créée, l’informant si les ressources qu’il vient d’être affectées sont occupées ou inactives à l’extérieur.

## <a name="ischedulernotifyresourcesexternallyidle-method"></a><a name="notifyresourcesexternallyidle"></a>IScheduler::NotifyResourcesExternallyIdle Méthode

Informe ce planificateur que les fils matériels représentés par l’ensemble des racines du processeur virtuel dans le tableau `ppVirtualProcessorRoots` ne sont pas utilisés par d’autres planificateurs.

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Paramètres

*ppVirtualProcessorRoots*<br/>
Un éventail `IVirtualProcessorRoot` d’interfaces associées aux fils matériels sur lesquels d’autres planificateurs sont devenus inactifs.

*count*<br/>
Le nombre `IVirtualProcessorRoot` d’interfaces dans le tableau.

### <a name="remarks"></a>Notes

Il est possible qu’un thread matériel particulier soit affecté à plusieurs planificateurs en même temps. Une raison à cela pourrait être qu’il n’y a pas assez de fils matériels sur le système pour satisfaire la concurrence minimale pour tous les planificateurs, sans partager les ressources. Une autre possibilité est que les ressources sont temporairement affectées à d’autres planificateurs lorsque le planificateur propriétaire ne les utilise pas, par le moyen de toutes ses racines de processeur virtuel sur ce fil matériel étant désactivé.

Le niveau d’abonnement d’un thread matériel est indiqué par le nombre de threads abonnés et les racines de processeur virtuel activé associées à ce fil matériel. Du point de vue d’un planificateur particulier, le niveau d’abonnement externe d’un thread matériel est la partie de l’abonnement auquel les autres planificateurs contribuent. Les notifications indiquant que les ressources sont occupées à l’extérieur sont envoyées à un planificateur lorsque le niveau d’abonnement externe pour un thread matériel tombe à zéro par rapport à une valeur positive antérieure.

Les notifications par cette méthode ne sont envoyées qu’aux planificateurs qui ont une politique où la valeur de la `MinConcurrency` clé de stratégie est égale à la valeur de la `MaxConcurrency` clé de la stratégie. Pour plus d’informations sur les politiques de planificateur, voir [SchedulerPolicy](schedulerpolicy-class.md).

Un planificateur qui est admissible aux notifications reçoit un ensemble de notifications initiales lorsqu’elle est créée, l’informant si les ressources qu’il vient d’être affectées sont occupées ou inactives à l’extérieur.

## <a name="ischedulerremovevirtualprocessors-method"></a><a name="removevirtualprocessors"></a>IScheduler::RemoveVirtualProcessors Méthode

Initie la suppression des racines de processeur virtuel qui ont été précédemment allouées à ce planificateur.

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>Paramètres

*ppVirtualProcessorRoots*<br/>
Un éventail `IVirtualProcessorRoot` d’interfaces représentant les racines du processeur virtuel à supprimer.

*count*<br/>
Le nombre `IVirtualProcessorRoot` d’interfaces dans le tableau.

### <a name="remarks"></a>Notes

Le gestionnaire des `RemoveVirtualProcessors` ressources invoque la méthode pour reprendre un ensemble de racines de processeur virtuel d’un planificateur. On s’attend à ce que le planificateur invoque la méthode [Supprimer](iexecutionresource-structure.md#remove) sur chaque interface quand elle est faite avec les racines de processeur virtuel. N’utilisez `IVirtualProcessorRoot` pas d’interface une `Remove` fois que vous avez invoqué la méthode sur elle.

Le `ppVirtualProcessorRoots` paramètre indique un éventail d’interfaces. Parmi l’ensemble des racines de processeur virtuel à enlever, les racines `Remove` n’ont jamais été activées peuvent être retournées immédiatement en utilisant la méthode. Les racines qui ont été activées et qui exécutent des travaux, ou qui ont été désactivées et qui attendent l’arrivée du travail, doivent être retournées de façon asynchrone. Le planificateur doit faire toutes les tentatives pour enlever la racine du processeur virtuel aussi rapidement que possible. Retarder l’élimination des racines du processeur virtuel peut entraîner une sursubscription involontaire au sein du planificateur.

## <a name="ischedulerstatistics-method"></a><a name="statistics"></a>IScheduler::Méthode des statistiques

Fournit de l’information sur les taux d’arrivée et d’achèvement des tâches et des changements dans la longueur des files d’attente pour un planificateur.

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>Paramètres

*pTaskCompletionRate*<br/>
Le nombre de tâches qui ont été accomplies par le planificateur depuis le dernier appel à cette méthode.

*pTaskArrivalRate*<br/>
Le nombre de tâches qui sont arrivées dans le planificateur depuis le dernier appel à cette méthode.

*pNumberOfTasksEnqueued*<br/>
Le nombre total de tâches dans toutes les files d’attente des planificateurs.

### <a name="remarks"></a>Notes

Cette méthode est invoquée par le gestionnaire des ressources afin de recueillir des statistiques pour un planificateur. Les statistiques recueillies ici seront utilisées pour générer des algorithmes de rétroaction dynamique afin de déterminer quand il convient d’affecter plus de ressources au planificateur et quand retirer des ressources. Les valeurs fournies par le planificateur peuvent être optimistes et ne doivent pas nécessairement refléter le décompte actuel avec précision.

Vous devez mettre en œuvre cette méthode si vous voulez que le gestionnaire de ressources utilise les commentaires sur des choses telles que l’arrivée des tâches pour déterminer comment équilibrer les ressources entre votre planificateur et les autres planificateurs inscrits auprès du gestionnaire des ressources. Si vous choisissez de ne pas recueillir `DynamicProgressFeedback` de statistiques, vous pouvez définir la clé de la stratégie de la valeur `DynamicProgressFeedbackDisabled` de la police de votre planificateur, et le gestionnaire des ressources n’invoquera pas cette méthode sur votre planificateur.

En l’absence d’informations statistiques, le gestionnaire des ressources utilisera les niveaux d’abonnement aux fils matériels pour prendre des décisions en matière d’allocation des ressources et de migration. Pour plus d’informations sur les niveaux d’abonnement, voir [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).

## <a name="see-also"></a>Voir aussi

[accès concurrentiel Namespace](concurrency-namespace.md)<br/>
[PolitiqueElementKey](concurrency-namespace-enums.md)<br/>
[Classe SchedulerPolicy](schedulerpolicy-class.md)<br/>
[IExecutionContext, structure](iexecutioncontext-structure.md)<br/>
[IThreadProxy, structure](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot, structure](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager, structure](iresourcemanager-structure.md)
