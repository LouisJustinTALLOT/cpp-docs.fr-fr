---
title: IScheduler, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c78d02ccd5639369ad8b4d0183458da2ba85269
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693989"
---
# <a name="ischeduler-structure"></a>IScheduler, structure
Interface avec une abstraction d'un planificateur de tâches. Le gestionnaire des ressources du runtime d'accès concurrentiel utilise cette interface pour communiquer avec les planificateurs de tâches.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IScheduler;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IScheduler::AddVirtualProcessors](#addvirtualprocessors)|Fournit un planificateur avec un ensemble de racines de processeur virtuel pour son utilisation. Chaque `IVirtualProcessorRoot` interface représente le droit d’exécuter un thread unique qui peut effectuer un travail pour le compte du planificateur.|  
|[IScheduler::GetId](#getid)|Retourne un identificateur unique pour le planificateur.|  
|[IScheduler::GetPolicy](#getpolicy)|Retourne une copie de la stratégie du planificateur. Pour plus d’informations sur les stratégies de planificateur, consultez [SchedulerPolicy](schedulerpolicy-class.md).|  
|[IScheduler::NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|Notifie ce planificateur que les threads matériels représentés par l’ensemble de racines de processeur virtuel dans le tableau `ppVirtualProcessorRoots` est maintenant utilisé par d’autres planificateurs.|  
|[IScheduler::NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|Notifie ce planificateur que les threads matériels représentés par l’ensemble de racines de processeur virtuel dans le tableau `ppVirtualProcessorRoots` ne sont pas utilisés par d’autres planificateurs.|  
|[IScheduler::RemoveVirtualProcessors](#removevirtualprocessors)|Lance la suppression des racines de processeur virtuel qui ont été précédemment alloué à ce planificateur.|  
|[IScheduler::Statistics](#statistics)|Fournit des informations relatives aux taux d’arrivée et l’achèvement de tâche et la modification de la longueur de file d’attente pour un planificateur.|  
  
## <a name="remarks"></a>Notes  
 Si vous implémentez un planificateur personnalisé qui communique avec le Gestionnaire de ressources, vous devez fournir une implémentation de la `IScheduler` interface. Cette interface est une extrémité d’un canal bidirectionnel de communication entre un planificateur et le Gestionnaire de ressources. L’autre extrémité est représentée par le `IResourceManager` et `ISchedulerProxy` les interfaces qui sont implémentées par le Gestionnaire de ressources.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IScheduler`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** concrtrm.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="addvirtualprocessors"></a>  IScheduler::AddVirtualProcessors, méthode  
 Fournit un planificateur avec un ensemble de racines de processeur virtuel pour son utilisation. Chaque `IVirtualProcessorRoot` interface représente le droit d’exécuter un thread unique qui peut effectuer un travail pour le compte du planificateur.  
  
```
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `ppVirtualProcessorRoots`  
 Un tableau de `IVirtualProcessorRoot` racines d’interfaces qui représente le processeur virtuel ajouté au planificateur.  
  
 `count`  
 Le nombre de `IVirtualProcessorRoot` interfaces dans le tableau.  
  
### <a name="remarks"></a>Notes  
 Le Gestionnaire de ressources appelle la `AddVirtualProcessor` méthode pour accorder un ensemble initial de racines de processeur virtuel à un planificateur. Il peut également appeler la méthode pour ajouter des racines de processeur virtuel au planificateur lorsqu’il redistribue les ressources entre les planificateurs.  
  
##  <a name="getid"></a>  IScheduler::GetId, méthode  
 Retourne un identificateur unique pour le planificateur.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un identificateur entier unique.  
  
### <a name="remarks"></a>Notes  
 Vous devez utiliser le [GetSchedulerId](concurrency-namespace-functions.md) fonction pour obtenir un identificateur unique pour l’objet qui implémente le `IScheduler` interface, avant d’utiliser l’interface en tant que paramètre aux méthodes fournies par le Gestionnaire de ressources. Vous devez retourner le même identificateur lorsque la `GetId` fonction est appelée.  
  
 Un identificateur obtenu à partir d’une autre source peut entraîner un comportement non défini.  
  
##  <a name="getpolicy"></a>  IScheduler::GetPolicy, méthode  
 Retourne une copie de la stratégie du planificateur. Pour plus d’informations sur les stratégies de planificateur, consultez [SchedulerPolicy](schedulerpolicy-class.md).  
  
```
virtual SchedulerPolicy GetPolicy() const = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une copie de la stratégie du planificateur.  
  
##  <a name="notifyresourcesexternallybusy"></a>  IScheduler::NotifyResourcesExternallyBusy, méthode  
 Notifie ce planificateur que les threads matériels représentés par l’ensemble de racines de processeur virtuel dans le tableau `ppVirtualProcessorRoots` est maintenant utilisé par d’autres planificateurs.  
  
```
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `ppVirtualProcessorRoots`  
 Un tableau de `IVirtualProcessorRoot` interfaces associées aux threads matériels sur lesquels d’autres planificateurs sont actifs.  
  
 `count`  
 Le nombre de `IVirtualProcessorRoot` interfaces dans le tableau.  
  
### <a name="remarks"></a>Notes  
 Il est possible pour un thread matériel particulier être assigné à plusieurs planificateurs en même temps. Une des raisons est peut-être qu’il ne sont pas assez de threads matériels sur le système pour satisfaire l’accès concurrentiel minimal pour tous les planificateurs, sans partage de ressources. Il est également possible que les ressources sont temporairement attribués à d’autres planificateurs lorsque le planificateur propriétaire n’utilise pas, au moyen de toutes ses racines de processeur virtuel sur ce thread matériel en cours de désactivation.  
  
 Le niveau d’abonnement d’un thread matériel est représentée par le nombre de threads auxquels vous êtes abonnés et activé pour les racines de processeur virtuel associés à ce thread matériel. Du point de vue d’un planificateur spécifique, le niveau d’abonnement externe d’un thread matériel est la partie de l’abonnement à qu'autres planificateurs contribuent. Les notifications que les ressources sont occupées à l’extérieur sont envoyées à un planificateur lorsque le niveau d’abonnement externe d’un thread matériel se déplace à partir de zéro dans territoire positif.  
  
 Les notifications via cette méthode sont envoyées uniquement aux planificateurs qui ont une stratégie où la valeur de la `MinConcurrency` clé de la stratégie est égale à la valeur de la `MaxConcurrency` clé de stratégie. Pour plus d’informations sur les stratégies de planificateur, consultez [SchedulerPolicy](schedulerpolicy-class.md).  
  
 Un planificateur qualifié pour les notifications Obtient un jeu de notifications initiales lorsqu’il est créé, informant si les ressources qu’il vient d’assigner sont en externe occupé ou inactif.  
  
##  <a name="notifyresourcesexternallyidle"></a>  IScheduler::NotifyResourcesExternallyIdle, méthode  
 Notifie ce planificateur que les threads matériels représentés par l’ensemble de racines de processeur virtuel dans le tableau `ppVirtualProcessorRoots` ne sont pas utilisés par d’autres planificateurs.  
  
```
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `ppVirtualProcessorRoots`  
 Un tableau de `IVirtualProcessorRoot` interfaces associées aux threads matériels sur lesquels d’autres planificateurs sont inactifs.  
  
 `count`  
 Le nombre de `IVirtualProcessorRoot` interfaces dans le tableau.  
  
### <a name="remarks"></a>Notes  
 Il est possible pour un thread matériel particulier être assigné à plusieurs planificateurs en même temps. Une des raisons est peut-être qu’il ne sont pas assez de threads matériels sur le système pour satisfaire l’accès concurrentiel minimal pour tous les planificateurs, sans partage de ressources. Il est également possible que les ressources sont temporairement attribués à d’autres planificateurs lorsque le planificateur propriétaire n’utilise pas, au moyen de toutes ses racines de processeur virtuel sur ce thread matériel en cours de désactivation.  
  
 Le niveau d’abonnement d’un thread matériel est représentée par le nombre de threads auxquels vous êtes abonnés et activé pour les racines de processeur virtuel associés à ce thread matériel. Du point de vue d’un planificateur spécifique, le niveau d’abonnement externe d’un thread matériel est la partie de l’abonnement à qu'autres planificateurs contribuent. Les notifications que les ressources sont occupées à l’extérieur sont envoyées à un planificateur lorsque le niveau d’abonnement externe d’un thread matériel tombe à zéro à partir d’une valeur positive précédente.  
  
 Les notifications via cette méthode sont envoyées uniquement aux planificateurs qui ont une stratégie où la valeur de la `MinConcurrency` clé de la stratégie est égale à la valeur de la `MaxConcurrency` clé de stratégie. Pour plus d’informations sur les stratégies de planificateur, consultez [SchedulerPolicy](schedulerpolicy-class.md).  
  
 Un planificateur qualifié pour les notifications Obtient un jeu de notifications initiales lorsqu’il est créé, informant si les ressources qu’il vient d’assigner sont en externe occupé ou inactif.  
  
##  <a name="removevirtualprocessors"></a>  IScheduler::RemoveVirtualProcessors, méthode  
 Lance la suppression des racines de processeur virtuel qui ont été précédemment alloué à ce planificateur.  
  
```
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `ppVirtualProcessorRoots`  
 Un tableau de `IVirtualProcessorRoot` les interfaces qui représentent les racines de processeur virtuel à supprimer.  
  
 `count`  
 Le nombre de `IVirtualProcessorRoot` interfaces dans le tableau.  
  
### <a name="remarks"></a>Notes  
 Le Gestionnaire de ressources appelle la `RemoveVirtualProcessors` méthode afin de reprendre un ensemble de racines de processeur virtuel à partir d’un planificateur. Le planificateur est supposé appeler la [supprimer](iexecutionresource-structure.md#remove) méthode sur chaque interface lorsqu’il est terminé avec les racines de processeur virtuel. N’utilisez pas un `IVirtualProcessorRoot` interface une fois que vous avez appelé la `Remove` méthode dessus.  
  
 Le paramètre `ppVirtualProcessorRoots` pointe vers un tableau d’interfaces. Dans le jeu de racines de processeur virtuel à supprimer, les racines n’ont jamais été activées peuvent être retournées immédiatement à l’aide du `Remove` (méthode). Les racines qui ont été activés et sont en cours d’exécution travailler, ou ont été désactivées et sont en attente d’un travail arrive, doivent être retournées de façon asynchrone. Le planificateur doit faire en sorte de supprimer la racine de processeur virtuel aussi rapidement que possible. Retarder la suppression de racines de processeur virtuel risque de surabonnement involontaire dans le planificateur.  
  
##  <a name="statistics"></a>  IScheduler::STATISTICS, méthode  
 Fournit des informations relatives aux taux d’arrivée et l’achèvement de tâche et la modification de la longueur de file d’attente pour un planificateur.  
  
```
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `pTaskCompletionRate`  
 Le nombre de tâches qui ont été effectuées par le planificateur depuis le dernier appel à cette méthode.  
  
 `pTaskArrivalRate`  
 Le nombre de tâches qui sont arrivés dans le planificateur depuis le dernier appel à cette méthode.  
  
 `pNumberOfTasksEnqueued`  
 Le nombre total de tâches dans toutes les files d’attente du planificateur.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par le Gestionnaire de ressources pour collecter des statistiques pour un planificateur. Les statistiques collectées ici permet de lecteur des algorithmes de retour dynamique pour déterminer quand il convient d’assigner plus de ressources au planificateur et quand effectuer immédiatement des ressources. Les valeurs fournies par le planificateur peuvent être optimistes et n’ont pas nécessairement afin de refléter le nombre actuel avec précision.  
  
 Vous devez implémenter cette méthode si vous souhaitez que le Gestionnaire de ressources à utiliser des commentaires à propos des éléments tels que l’arrivée de la tâche pour déterminer comment équilibrer la ressource entre votre planificateur et d’autres planificateurs inscrits avec le Gestionnaire de ressources. Si vous choisissez de ne pas collecter les statistiques, vous pouvez définir la clé de stratégie `DynamicProgressFeedback` à la valeur `DynamicProgressFeedbackDisabled` dans la stratégie et la ressource Manager n’appellera pas cette méthode de votre planificateur.  
  
 En l’absence d’informations statistiques, le Gestionnaire de ressources utilisera des niveaux d’abonnement thread matériel pour prendre des décisions d’allocation et la migration de ressources. Pour plus d’informations sur les niveaux d’abonnement, consultez [IExecutionResource::CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [SchedulerPolicy, classe](schedulerpolicy-class.md)   
 [IExecutionContext, Structure](iexecutioncontext-structure.md)   
 [IThreadProxy, Structure](ithreadproxy-structure.md)   
 [IVirtualProcessorRoot, Structure](ivirtualprocessorroot-structure.md)   
 [IResourceManager, structure](iresourcemanager-structure.md)
